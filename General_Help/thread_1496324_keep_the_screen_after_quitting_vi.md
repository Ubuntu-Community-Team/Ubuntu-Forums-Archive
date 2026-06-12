---
title: "keep the screen after quitting vi"
date: 2010-05-29
forum: General Help
---

### Post by orbita on 2010-05-29
hi, I have a little problem with vi in ubuntu 9.10. I searched but couldn't find any related topic. Hope some body would help. Thanks.

Whenever I exit vi, the terminal closes vi and goes back to the screen before vi. The content that I have just edited is not visible. 
How can I keep the content visible so that I can scroll back to view it even after I have exited vi?

---

### Post by jamesa00789 on 2010-05-29
Why don't you use *nano* instead of vi?

---

### Post by CharlesA on 2010-05-29
> **jamesa00789 said:**
> Why don't you use *nano* instead of vi?

nano does the same thing.

You could just run cat on whatever file you just edited and do it that way.

---

### Post by bulwynkl on 2010-05-29
first off - the folks saying "use nano" have no understanding of history - next they will be telling you how great emacs is or something....

I have the same issue with man pages...

so far I have traced the issue down to the pager, less...

there is an option you can set in less that prevents this..

       -X or --no-init
              Disables sending the termcap initialization and deinitialization strings to the terminal.  This is  sometimes  desirable  if  the deinitialization  string does something unnecessary, like clear&#8208;ing the screen.


i.e. if you invoke 

man -P 'less -X' man

(display the man page for man, using the pager 'less -X')
then quit, the man page text is persistent....

however, this raises the next issue - how to get this to occur everytime...

normally I add a line to .cshrc or .shrc or even .profile that set the environment variable for LESS

e.g. as specified in the man page for LESS

       Options are also taken from the environment variable "LESS".  For example, to avoid typing "less -options ..." each time less is invoked, you might tell csh:

       setenv LESS "-options"

       or if you use sh:

       LESS="-options"; export LESS

however, setenv seems to be missing in ubuntu... and setting up a .shrc also has not helped

bulwynkl@Sol:~$ setenv LESS "-X"
No command 'setenv' found, did you mean:
 Command 'netenv' from package 'netenv' (universe)
setenv: command not found

the command 'env' seems to do what it used to and includes two possible variables, LESSOPEN and LESSCLOSE - which both point to lesspipe - the man page for which is not really much help in this regards...




so, can someone point me to a resource that discusses exactly how ubuntu (specifically ubuntu 10.4, not unix in general) has been organised with respect to shells, pagers and environment variables.

just when you get a handle on how something is organised, someone comes up with a better way... I don mind - it's when they forget to tell anybody that is really bloody annoying

---

### Post by bulwynkl on 2010-05-29
this may help with setting the appropriate variables...

[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)

---

### Post by david_cuenca on 2010-08-20
For the "man" problem, you can change the "pager" behaviour in the man configuration file:

[LIST=1]
[*]Alt+F2
[*]```
gksudo gedit /etc/manpath.config
```
[*]Change the line
```
#DEFINE 	pager	pager -s
```
for
```
DEFINE 	pager	pager -X -s
```
[/LIST]

---

### Post by blur xc on 2010-08-20
I find sometimes it's desirable to have the man page (or the vi window) go away after exiting the program, and sometimes I like it to persist.  IMO, the best solution- is two terminal windows, or split windows ala terminator.  Then you can simply alt-tab or ctrl-tab (depending on your method) to either run commands, edit the text file, or view the man pages.

BM

---

### Post by spibou on 2010-08-20
> **bulwynkl said:**
> 
however, setenv seems to be missing in ubuntu... and setting up a .shrc also has not helped

bulwynkl@Sol:~$ setenv LESS "-X"
No command 'setenv' found, did you mean:
 Command 'netenv' from package 'netenv' (universe)
setenv: command not found
I just tried **setenv LESS "-X"** from the tcsh command line and it worked fine. Regarding .shrc , which shell are you using and where did you put .shrc ?
> so, can someone point me to a resource that discusses exactly how ubuntu (specifically ubuntu 10.4, not unix in general) has been organised with respect to shells, pagers and environment variables.
I doubt that Ubuntu does anything special with regards to shells and environment variables. The man page of the shell you're using will likely have an "invocation" section which tells you which initialisation scripts get executed and in which order. Regarding pagers, do **whereis pager** and it will tell you which programme gets executed.

---

### Post by spibou on 2010-08-20
> **orbita said:**
> hi, I have a little problem with vi in ubuntu 9.10. I searched but couldn't find any related topic. Hope some body would help. Thanks.

Whenever I exit vi, the terminal closes vi and goes back to the screen before vi. The content that I have just edited is not visible. 
How can I keep the content visible so that I can scroll back to view it even after I have exited vi?
Try the advice at [http://www.shallowsky.com/linux/noaltscreen.html](http://www.shallowsky.com/linux/noaltscreen.html)

---

