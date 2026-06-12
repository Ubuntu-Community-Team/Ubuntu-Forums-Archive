---
title: "Creation of a prompt without using Qt"
date: 2010-03-12
forum: General Help
---

### Post by ngrieb on 2010-03-12
I'm working on a rather large Fortran code at work, which takes a long time to run and sometimes crashes due to editing errors and such. I want a way of knowing that it has crashed while I'm working on a different workspace, and would like to insert a line of code that can create a prompt window to appear so that I know if it has stopped or crashed. 

The problem is that I'm pretty locked down by the admins here at work and only have java and html to work with (Qt is not installed). 

Is there anyway to tie some javascript or html into Fortran 90, and can I run html or javascript without openeing an entire browser window? I just want a small warning box to appear, and know how to code this in html.

BTW, what are the usual Fortran libs associated with making calls to the Linux terminal?

---

### Post by sandyd on 2010-03-12
> **ngrieb said:**
> I'm working on a rather large Fortran code at work, which takes a long time to run and sometimes crashes due to editing errors and such. I want a way of knowing that it has crashed while I'm working on a different workspace, and would like to insert a line of code that can create a prompt window to appear so that I know if it has stopped or crashed. 

The problem is that I'm pretty locked down by the admins here at work and only have java and html to work with (Qt is not installed). 

Is there anyway to tie some javascript or html into Fortran 90, and can I run html or javascript without openeing an entire browser window? I just want a small warning box to appear, and know how to code this in html.

BTW, what are the usual Fortran libs associated with making calls to the Linux terminal?
```

character :: command
command = "zenity --error --text "Error! ""
call system(command)
```
make sure your using the f95 standard when compiling.

---

### Post by ngrieb on 2010-03-12
Sweet. That works well for just an info prompt, but is there any way to also read back an answer from zenity to Fortran...say if I used a --question option like:

CALL SYSTEM("zenity --question --text "DELETE?"")

!Wait for a reply somehow? 
!Would the program wait for input from the system call?

IF (zenity_answer .EQ. 0) STOP

I assume this is possible via like a READ,* statement? Is this so?

---

### Post by sandyd on 2010-03-12
> **ngrieb said:**
> Sweet. That works well for just an info prompt, but is there any way to also read back an answer from zenity to Fortran...say if I used a --question option like:

CALL SYSTEM("zenity --question --text "DELETE?"")

!Wait for a reply somehow? 
!Would the program wait for input from the system call?

IF (zenity_answer .EQ. 0) STOP

I assume this is possible via like a READ,* statement? Is this so?
not sure about that, I only dabbled a bit in fortran

---

### Post by ngrieb on 2010-03-12
Well all I really need is a read in from the terminal if I could somehow echo the output, as far as I know. The problem is when I try and echo the output for the question button nothing happens. 
--question should return a 0 or 1 as noted in the man pages. Perhaps the call to system will take in the 0 or 1?...

---

### Post by rnerwein on 2010-03-13
hi
i don't know any thing about fortran but may this will help you ( zenity using in the bash ).
my script as an example:
#!/bin/bash
#
command=`zenity  --title "run a command" --entry --text "give me the command" --width 1000 --height 50`
$command | zenity --text-info --width 1000 --height 500 - I
exit 0

i can use this stuff in C and i guess it's possible in fortran too.
ciao

---

### Post by d3v1150m471c on 2010-03-13
Just use the native command [COLOR="DarkRed"]wall[/COLOR] instead of installing zenity.

---

### Post by ngrieb on 2010-03-14
Ok, so I read in most places that in Fortran

CALL SYSTEM("...command...", system_output)

Should take in the systems output from the command issued, however, I am getting a segfault when trying to use the ", system_output" variable in my code. I am using an ifort compiler (don't know which one, but not the latest). 

I can get the shell to echo the input like:
CALL SYSTEM('zen= zenity --warning --text "DELETE FILES"; echo $((zen))')

which echo's 1 or zero, but how can I read this into read or somehow get the Fortran process to stop if zen=0? 

Maybe a better option would be a way to kill the process using the shell script... Is there a way to shell script an:

 if(zen=0) kill [process_name], 

when the process name can vary due to renaming in the make file?

---

### Post by ngrieb on 2010-03-15
I found this on a website:

#!/bin/sh
zenity &#8211;question &#8211;text=&#8221;Do you wish to continue/?&#8221;
rc=$?
if [ "${rc}" == "1" ]; then
echo &#8220;Program terminated.&#8221;
exit 1
fi

which is pretty much what I need, but I keep getting an error like:
[: 9: 0: unexpected operator
What does it mean? What operator am I not using correctly? Sorry this is my first real dive into shell scripting. I'm having a hard time...

Ok, I got it.
It should be 

if [ $((rc)) -eq 1]
then
ttname=${tty};
pkill -t ${ttname:5}
fi

---

