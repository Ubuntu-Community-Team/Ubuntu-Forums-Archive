---
title: "Running scripts from USB key on 10.10"
date: 2011-07-01
forum: General Help
---

### Post by Bluztrvler on 2011-07-01
Greetings,

I have two computers running Ubuntu 10.10.  One has a DSL connection and the other is straddled with a dial up connection.  I update the dial-up computer using Synaptic's "Generate package download script" feature and it has worked well until I upgraded to 10.10 on the DSL computer.

I understand that the issue has to do with permissions, and allowing execution of files on removable media, and I have tried many different things, but no joy.

Here is what I have found.  If I copy the script to my desktop  on the DSL computer, I can make it executable and it will run, either by using the properties-permissions GUI, or by using the command line. However, neither of these things work with the file on the USB stick.  The command line doesn't report an error and appears to work, and the check mark on the GUI will appear then instantly disappear.  If I check the permissions on the usb stick itself, it says that it is executable, but clicking the "apply these settings to all enclosed files" does nothing to change the permissions of the script file.

I'm sure there is a simple way to make this work, It worked on previous versions of Ubuntu, but I cannot seem to find it.  Any help would be appreciated.


Just found this link.  It answered all my questions.  Many thanks.

[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

