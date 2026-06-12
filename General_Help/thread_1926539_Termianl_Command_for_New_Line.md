---
title: "Termianl Command for New Line"
date: 2012-02-16
forum: General Help
---

### Post by gr8 on 2012-02-16
What is the terminal command to give you a new line after the current command executes?

For example, I ofter have to run the command "unity &disown" and then a bunch of output keeps displaying and displaying forever. I want to can the output and just get a new command line. I used to do this but now forgot.

---

### Post by raja.genupula on 2012-02-16
> **gr8 said:**
> What is the terminal command to give you a new line after the current command executes?

For example, I ofter have to run the command "unity &disown" and then a bunch of output keeps displaying and displaying forever. I want to can the output and just get a new command line. I used to do this but now forgot.

* your post not clear , many spell mistakes . 
Well , any way what i understand from your post is you dont want to display a command's output you simply wanna get command prompt again after executing that command .

then do this 

you command  > output.txt

that commands output will be in the output.txt file.


CASE-2

suppose one command executing continuously and giving the output  as well  in terminal .If you wanna quit from cases like that then press CTRL+D or CTRL+C  ,to stop that and come back to terminal prompt . 

For more accurate 
CTRL+C -> will kills what ever running .
CTRL+D ->Exit the Current shell. 


NOTE: Next time on wards if you're posting anything please recheck your post before submit.  Thank you .

If anything comes up please let us know .

---

### Post by lykwydchykyn on 2012-02-16
nohup will do what you want:

```

nohup mycommand &disown

```

Though be advised it  will create a file called "nohup.out" in the current directory to hold the output.


you can also redirect to /dev/null, though make sure you redirect both stdout and stderr, like so:
```

mycommand &disown &>/dev/null

```

---

### Post by drmrgd on 2012-02-16
> **raja.genupula said:**
> * your post not clear , many spell mistakes . 
Well , any way what i understand from your post is you dont want to display a command's output you simply wanna get command prompt again after executing that command .

then do this 

you command  > output.txt

that commands output will be in the output.txt file.


CASE-2

suppose one command executing continuously and giving the output  as well  in terminal .If you wanna quit from cases like that then press CTRL+D or CTRL+C  ,to stop that and come back to terminal prompt . 

For more accurate 
CTRL+C -> will kills what ever running .
CTRL+D ->Exit the Current shell. 


NOTE: Next time on wards if you're posting anything please recheck your post before submit.  Thank you .

If anything comes up please let us know .

I think what you're looking for is almost like Raja's first suggestion, with one exception.  He is suggesting to launch the application and then pipe the output to "output.txt".  However, this will not free up the shell for more input.  You'll also need to add '&' in order to run the process in the background.  So, something like:

```
process & > /dev/null # to pipe the output to the void
process & > somefile.txt # to pipe the output to a file that you can look at later
```

---

### Post by gr8 on 2012-02-16
Exactly, i was looking for the command to run processes in the background, thus freeing the shell for new commands. It seems the correct answer is to place a "space" and "&" at the end of a command. For example.

command &

Thank you!

---

### Post by raja.genupula on 2012-02-16
Thats good news , please mark the thread as solved from  thread tools.
Thank you ,:)

---

### Post by lykwydchykyn on 2012-02-16
> **gr8 said:**
> Exactly, i was looking for the command to run processes in the background, thus freeing the shell for new commands. It seems the correct answer is to place a "space" and "&" at the end of a command. For example.

command &

Thank you!

The ampersand will run the command in the background, but it will not suppress any output from the command.  This can be annoying if you have a noisy process.

Adding "disown" means that the launched process is no longer a child of the terminal window -- so that if you close the terminal window, it won't also close the process.  Without that, any processes (background or foreground) launched from the terminal window close with it.

---

### Post by Khayyam on 2012-02-16
> **gr8 said:**
> [...]For example, I ofter have to run the command "unity &disown" and then a bunch of output keeps displaying and displaying forever. I want to can the output and just get a new command line. I used to do this but now forgot.

I think what your looking for is one of two things, you want to either "redirect" (send output ... stdout and stderr ... so you don't see it) or "background" (send that particular "job" into the background).

**Redirection:** here all output (stdout) and error messages (stderr) are sent to /dev/null (an empty nothingness). Note: stdout and stderr are denoted by "1" and "2" respectively.

```
cat input.txt 2>&1 > /dev/null
```

**Background:** here we background the "job" so the shell (command prompt) is returned. The "job" will carry on till completion, only in the background.

```
command &
```
[B]
Sometimes[/B] its useful to do both, in which case you can do the following:

```
cat input.txt 2>&1 > /dev/null &
```

**Job Control:** for jobs in the background you can re-call them by using the commands "jobs" and "fg" (foreground)

```
% less input.txt &
[1]  + 416 suspended (tty output) less input.txt
% jobs
[1]  + suspended (tty output)  less input.txt
% fg 1
```

Note I'm using zsh, and not bash, so the information presented may be a little different to what you see, but the commands are the same.

HTH ... khay

---

