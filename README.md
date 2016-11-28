# VTU OS Lab Programs

All of the VTU OS lab problems with solutions and instructions and how to run it.

Hopefully it'll help some someone who needs it the way I did.

## Shell Programs

### 7A

*Non-recursive shell script that accepts any number of arguments and prints them in the Reverse order, ( For example, if the script is named rargs, then executing rargs A B C should produce C B A on the standard output).*

#### Execution:

```shell
$ sh 7a_reverse_arguments.sh Hello World

Number of arguments is 2
The arguments are Hello World
The reverse is World Hello 
```

### 8A

*Shell script that accepts two file names as arguments, checks if the permissions for these files are identical and if the permissions are identical, outputs the common permissions, otherwise outputs each file name followed by its permissions.*

#### Execution

```shell
$ touch f1
$ touch f2
$ sh 8a_permissions.sh f1 f2

Identical permissions: rw-rw-r--

$ chmod u+x f1
$ sh 8a_permissions.sh f1 f2

Permissions are not identical
f1 permissions: rwxrw-r--
f2 permissions: rw-rw-r--
```

### 9A

*Shell script that accepts file names specified as arguments and creates a shell script that contains this file as well as the code to recreate these files. Thus if the script generated by your script is executed, it would recreate the original files.*

#### Execution

```shell
$ cat >f1
This is file f1
[Ctrl + D]

$ cat >f2
This is file f2
[Ctrl + D]

$ sh 9a_bundle.sh f1 f2
                                       
$ rm f1 f2
                                       
$ sh cr.sh
                                       
$ cat f1
This is file f1
                                 
$ cat f2
This is file f2

```

## C Programs

### 7B

*C program that creates a child process to read commands from the standard input and execute them (a minimal implementation of a shell – like program). You can assume that no arguments will be passed to the commands to be executed.*

#### Execution

```shell
$ cc 7b_run_commands.c
$ ./a.out

Child Process:
Enter the command: ls
7a_reverse_arguments.sh  8a_permissions.sh  a.out  f2          README.md
7b_run_commands.c        9a_bundle.sh       f1     LICENSE.md

Enter 0 to exit or 1 to continue: 1

Child Process:
Enter the command: date
Mon Nov 28 13:02:49 IST 2016

Enter 0 to exit or 1 to continue: 0
```

### 8B

*C program to create a file with 16 bytes of arbitrary data from the beginning and another 16 bytes of arbitrary data from an offset of 48. Display the file contents to demonstrate how the hole in file is handled.*

#### Execution

```shell
$ cc 8b_file_writing.c

$ ./a.out
0000000   1   2   3   4   5   6   7   8   9   a   b   c   d   e   f   g
0000020  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0
*
0000060   h   i   j   k   l   m   n   o   p   q   r   s   t   u   v   w
0000100
```

### 9B

*C program to do the following: Using fork( ) create a child process. The child process prints its own process-id and id of its parent and then exits. The parent process waits for its child to finish (by executing the wait( )) and prints its own process-id and the id of its child process and then exits.*

#### Execution

```shell
$ cc 9b_parent_child_pid.c

$ ./a.out
Child Process:
Parent PID: 21125
Child PID: 21126

Parrent Process:
Parent PID: 21125
Child PID: 21126
```

### 10

*Design, develop and execute a program in C / C++ to simulate the working of Shortest Remaining Time and Round-Robin Scheduling Algorithms. Experiment with different quantum sizes for the Round- Robin algorithm. In all cases, determine the average turn-around time. The input can be read from keyboard or from a file.*

#### Execution

```shell
$ cc 10_schedulers.c

$ ./a.out
1. Shortest job first
2. Round robin
> 1
How many processes: 4
Arrival times of processes: 0 1 2 3
Burst times of processes:   8 4 9 5

Average waiting time: 6.50
Average turn around time: 13.00

$ ./a.out
1. Shortest job first
2. Round robin
> 2
Number of processes: 3
Burst time of processes: 24 3 3
Time quantum: 4

PROCESS BURST TIME      WAITING TIME    TURN AROUND TIME
======= ==========      ============    =================
1               24              6               30
2               3               4               7
3               3               7               10

Average waiting time: 5.67
Average turn around time: 15.67

$ ./a.out
1. Shortest job first
2. Round robin
> 2
Number of processes: 3
Burst time of processes: 24 3 3
Time quantum: 3

PROCESS BURST TIME      WAITING TIME    TURN AROUND TIME
======= ==========      ============    =================
1               24              6               30
2               3               3               6
3               3               6               9

Average waiting time: 5.00
Average turn around time: 15.00
```

### 11

*Using OpenMP, Design, develop and run a multi-threaded program to generate and print Fibonacci Series. One thread has to generate the numbers up to the specified limit and another thread has to print them. Ensure proper synchronization.*

#### Execution

```shell
$ cc -fopenmp 11_thread_fibonacci.c 
adithya at thinkpad-t420 in ~/P/G/vtu-os-lab-Programs
                                       
$ ./a.out 
Enter the number of terms: 10
Thread 0 -- generated term number 3
Thread 0 -- generated term number 4
Thread 0 -- generated term number 5
Thread 0 -- generated term number 6
Thread 0 -- generated term number 7
Thread 0 -- generated term number 8
Thread 0 -- generated term number 9
Thread 0 -- generated term number 10

The series is:
Thread 1 -- generated term 0
Thread 1 -- generated term 1
Thread 1 -- generated term 1
Thread 1 -- generated term 2
Thread 1 -- generated term 3
Thread 1 -- generated term 5
Thread 1 -- generated term 8
Thread 1 -- generated term 13
Thread 1 -- generated term 21
Thread 1 -- generated term 34
```