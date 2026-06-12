---
title: "Sunbird integration with Ubuntu 10.04"
date: 2010-05-11
forum: General Help
---

### Post by quimkaos on 2010-05-11
Does anyone knows anyway to integrate Sunbird with Ubuntu 10.04? 
i'm not looking for integration of Sunbird with Thunderbird. that's accomplished with Lightning... What i  for is something like an alert when i have an event or even integration with the time/calendar Ubuntu standard application.

other thing is: I installed Sunbird... well not realy... it's a standalone... How can i add it the lists of known applications? like when i type Firefox in terminal Firefox pops up.

---

### Post by snoopy66 on 2010-05-13
To address your second question, if you wish to start Sunbird from a command prompt, the executable would have to be found in your PATH or you would have to specify the directory along with the command.  To see how your PATH is setup, go to the command prompt, and type:

echo $PATH

You should get something back similar to this:

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

You see that PATH contains a list of directories separated by colons (:).  When you type a command at the prompt, the system looks through your PATH, one directory at a time, to see if it can find the command that you entered.  If the command is located, the system runs it.  Otherwise, you get an error.

To see if a particular command is in your PATH, you can use the "which" command.  For example, issue the command:

which firefox

and you should get this result:

/usr/bin/firefox

Since "/usr/bin" is part of your PATH and the "firefox" command is located in this directory, the "which" command found it and displayed its location.  I suspect when you type:

which sunbird

you will get nothing in return, which means that the sunbird executable is not in any directory listed in your PATH.

Once you manually locate the executable, I'd recommend taking one of two actions:

1) Issue the command with the full path.  So, if you find the sunbird executable in the /opt/sb directory, enter the command "/opt/sb/sunbird" to start it.

2) Create a symbolic link to the sunbird executable in a directory that is in your PATH.  So again, if you find the sunbird executable in the /opt/sb directory, issue the following two commands:

cd /usr/bin
sudo ln -s /opt/sb/sunbird

Now you have a link in the /usr/bin directory, which is part of your PATH, that points to the actual executable.  So next time you issue the command "sunbird," the system will find it in /usr/bin and run it.  To test the link after you create it, you could use the "which" command (i.e., "which sunbird").  You should get this result:

/usr/bin/sunbird

Hope that helps!

(Incidentally, another option that I would not recommend would be to add the directory where sunbird is found to your PATH variable.)

---

### Post by quimkaos on 2010-05-13
Thank you! it did help!
and learned/remembered one thing or two!

just need someway to get an "widget" so i can have alerts when i have an event (like the mail notification)

---

