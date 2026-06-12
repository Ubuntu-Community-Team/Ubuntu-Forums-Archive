---
title: "C++: can't pass system output to variable"
date: 2010-09-08
forum: General Help
---

### Post by d3v1150m471c on 2010-09-08
I have a line that looks something like this:
```

system(cmd.c_str())

```How do i put its output in a variable?

---

### Post by harrismh777 on 2010-09-08
The system() command processor function takes a const char* which should be a zString, and returns an int. 

If you are interested in the return code like this:
   int rc=0;

   rc = system("ls -Al");

Remember that the return code is implementation dependent but usually indicates whether a command processor was present to handle the command string.

If you are interested in the output of the system call (the output from the command string passed to the command processor) then that depends are a host of factors.

First make sure you understand what you're doing... this:

   system("ls -Al")

  ... will hand the  ls -Al  command to the command processor in the current shell where the compiled code was run. If you add that command to your helloworld program it should print Hello,World! and then list the contents of the current directory to standard output.
   Now, if you are wanting to know how to save that output to a variable, well now, that depends... do you want it in a linked list of char* ? 
   You could use interprocess communication and pipe the output , or you could pipe the output to a file and then read the file, or you could place the output in shared memory area and pipe it... there are all kinds of creative ways to play with this... not sure it this helps.

   :???:

---

### Post by d3v1150m471c on 2010-09-08
Optimally i'd want the output in a string so that i could compare it with another string and direct the program from there. i'll have to apologize upfront for not being more clear. C++ is a language i am still learning. Thanks for your help.

---

### Post by harrismh777 on 2010-09-08
ok. Well, c++ is based on c , and with gnu c/c++ what you can do in c you can do in c++. (although, it may not be the best way to do things)

int system(const char*) is a standard C function found in stdlib.h

The function passes a string to the environment to be executed by a command processor if one exists. If the output from the command normally goes to standard out (and most of them do) then the output will be on standard out. The command processor will execute the command just as it would if you had typed the command on a terminal command line directly into bash. The command you send to system() could contain pipe characters so that the output is saved to a file, for instance... like so:

  system("ls -Al > myfilelist")

Now, instead of listing the current directory contents to standard output the contents will be listed in a file called "myfilelist".

Your program could then stat the file and if exist open the file and read the contents into a structure, linked list, what have you (obviously depending on your expected output and other details.

You could also pipe the output to a shared memory area... saves actually writing the output to a real disk location. 

--------------------------------------

Maybe there is a better way to accomplish what you're looking to for. In your example, what is cmd.string?

---

### Post by d3v1150m471c on 2010-09-09
> **harrismh777 said:**
> 
You could also pipe the output to a shared memory area... saves actually writing the output to a real disk location. 

How would I go about that? This is bascially what I'm trying to do:

```

cmd=`echo 'something'`

if [[ $cmd == *something* ]]; then
   do something
else
   do something
fi

```

---

### Post by harrismh777 on 2010-09-09
Ok, lets get to the answer in just a bit, but first you might want to consider whether using a system call would be better... these are the calls to the system (not command processor) and are fund in unistd.h

Ok, for the answer to the memory mapping question: first know this, its an advanced topic. Your are going to want to pick up a copy of Michael K. Johnson & Erik W. Troan's book "Linux Application Development",  or equiv.

Chapter (8) handles system calls, and unistd.h

Chapter (9) handles the process model

Chapter (12) ...this is where it gets interesting handles input and output multiplexing

Chapter (12.2 ff) discusses memory mapping, mapping regions, locking, syncing, etc.

   From the book, Linux allows a process to map files into its address space. Such a mapping creates a one-to-one correspondence between data in the file and data in the mapped memory region. ... files can be treated just like memory and read using pointers instead of system calls ... memory mapping allows processes to share memory regions that persist across process creation and destruction. The memory contents are stored in the mapped file, making it independent of any process.

   Yes, they have code examples. But here is the idea put alittle simpler to get the discussion and/or interest going. You can pass your command string to the command processor with system(), piping standard out to one of your newly mapped files. This memory region may persist across program invocations and may be accessed by other processes, or even the creating process.  The output can then be accessed directly with pointers, like any other memory space. Or, alternatively, it can be accessed with read() write() etc.

   You can even lock mapped memory regions. ... section 12.2.5

   There are several ways to map the region:
   MAP_ANONYMOUS
   MAP_FIXED
   MAP_PRIVATE    must have one of these
   MAP_SHARED     must have one of these
   MAP_DENYWRITE
   MAP_GROWSDOWN
   MAP_LOCKED

   You will need to research this a bit... and, I warn you, its not a beginning topic. Check out the book (should have it in your library) or do some snooping on-line for a tutorial... google is our friend.

   Hope this helps


:-\"

---

### Post by d3v1150m471c on 2010-09-09
Yay, got it!
```

string t1, t2;
t1 = system("echo something");
t2 = "something";

if (t1.compare (t2) ==0)
{
cout << "the output matches the test string!" << endl;
}
else
{
cout << "the output doesn't match the test string" << endl;
}

```

---

### Post by d3v1150m471c on 2010-09-09
thanks for all your help. i'll look into that book. the concept sounds fascinating

---

### Post by harrismh777 on 2010-09-09
> **d3v1150m471c said:**
> 
```

string t1, t2;
t1 = system("echo something");
t2 = "something";


```

Only problem is, that system() doesn't return a string.

You should have received a compile error on:

 t1 = system("echo something");

---

### Post by d3v1150m471c on 2010-09-12
no compilation errors except i've found it doesn't actually contain the system's output in the strings.

---

### Post by Noz3001 on 2010-09-12
Open a terminal and "man 3 popen". Maybe that will work for you.

---

### Post by d3v1150m471c on 2010-09-13
i'm just going to call a bash script with system and have it do my dirty work. i've been trying for a solid week now to do this using sprintf, system, and popen with no success. granted, i learned C++ from a pdf file and i've written maybe 2 infinitesimal programs with it. bash to the rescue !

---

