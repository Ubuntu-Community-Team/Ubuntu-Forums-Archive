---
title: "How can I use sudo in a startup script file?"
date: 2010-09-29
forum: General Help
---

### Post by bdemers on 2010-09-29
I am using a headless server with virtualbox installed on it.  A second box is a LAMP server from which I have phpvirtualbox installed to give me a remote connection to the headless server.  In order to get a connection made between the 2 boxes I need to start a program called vboxwebsrv, this being on the headless box.  I therefore need to ssh into the server and startup the program.  What I'd like to do is have this program launch on startup, and the folks at phpvirtualbox has a sample script available that will do that.  Unfortunately the script uses a su command, not sudo.  Since I am using Ubuntu, the su command doesn't work, but using sudo requires a password response.  How do I deal with this?

Here's a snippet from the script:

# Function that starts the daemon/service
#
do_start()
{
   if [ "$VBPID" != "" ] && [ "$VBPID" -gt 0 ]; then
      echo $NAME already running with PID $VBPID
   else
      su ${USER} -c 'vboxwebsrv -b --logfile /dev/null >/dev/null'
   fi
}

What I currently do is: sudo /usr/bin/vboxwebsrv -b --logfile /dev/null >/dev/null.
(The script file sets up the path earlier on).
What I don't want to do is have any interaction during startup, and frankly, I can't see how to avoid the password thing.

Can someone please give this newb some guidance, here?

---

### Post by luvshines on 2010-09-29
Sudo has options from where you can setup nopasswd for some (or ALL) commands/scripts/executables etc for particular groups/users

Maybe here you can find your answers:
[http://www.sudo.ws/sudo/sudoers.man.html](http://www.sudo.ws/sudo/sudoers.man.html)

---

### Post by psusi on 2010-09-29
That script is using su to run the program as some specific user.  Presumably it is intended to already be run by root, and switch to a less privileged user.  You should not modify it to use sudo.

There are two different things su does.  One is become the super user, and the other is become some other user.  The first requires the root password ( which doesn't exist on a default Ubuntu install ), the second does not require a password when you already are root.

---

### Post by bdemers on 2010-09-29
Looking over the document pointed out to me (thank you for that, by the way, I am new at all of this) I didn't come up with anything that seemed straight forward.  A couple of things here.  command line I issue has the computer up and running, and my already being logged on.  So a user has been assigned and it is here that I can understand how sudoers nopassword commands would be effective.  What concerns me however is that during startup of the computer, I have yet to be logged on, there is no user assigned so how do I deal with that?  I would assume that the script that I am trying to mod works just fine with a different distro, Debian, perhaps (a guess, is all).  My command line seems useless during load up of the opsys.  I need a different way to approach this.  I am way too new to guess what that would be, however

---

### Post by luvshines on 2010-09-29
As psusi rightly said, if the script is being run by root itself at the startup, you won't need to sudo otherwise you would.

How are you adding the script to startup ?

---

### Post by bdemers on 2010-09-29
Based on the posts I received, I figured that using changing the user name from vbox to one which is valid was worth a try.  It worked! 
Thanks for the comments, they helped a lot.

---

