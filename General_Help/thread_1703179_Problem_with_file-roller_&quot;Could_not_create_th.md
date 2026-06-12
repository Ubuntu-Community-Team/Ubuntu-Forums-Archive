---
title: "Problem with file-roller &quot;Could not create the archive&quot;"
date: 2011-03-08
forum: General Help
---

### Post by manerfiro on 2011-03-08
Hello, everybody I am using Ubuntu 10.10 and I started to have a kind of annoying problem with file-roller. I do not know what I attempted to unpack or pack form my USB HDD a couple of days ago, but when I did I got a message from the archive manager, the message was: "Could not create the archive, Archive type not supported."

Well, I just shrugged, and continued doing whatever I was doing, but later I noticed that whenever I tried to open the HDD for whatever reason from "PLACES" in the main panel, I was getting the same error message over and over again. It is not produced when I open the HDD from the Desktop link in my Desktop, that link will open the HDD with no problems, but if I try to access the HDD from "PLACES" in the main panel I will always get the same error message. This might be a small thing but it is driving me crazy.  :(

OK, what have I tried: since the archive manager window shows the "file-roller" logo in the menu button, I assumed that file roller is stuck with the previous process for which it produced an error, therefore I tried to "kill" any pending processes by several ways: Loggin-off, re-starting and turning the computer off. That did not worked. Whenever I attempted to open the HDD from "PLACES" the same error "Could not create the archive, Archive type not supported." will return.

Assuming that nautilus was stuck with the process i tried to kill any pending processes 
by using Alt+F2 and trying to kill the pending nautilus process using 

ps -e | grep nautilus 

and then the command

kill {####}

That did not worked either.

I was tired and uninstalled "file-roller" using the software manager, this solved the problem. But I actually use "file-roller" so I re-install the program and the problem returned.
I tried to uninstall the program using synaptic manager using the "Mark for complete removal" option, uninstall, re-install and the problem was there.
I uninstalled all the other recommended packages that were installed along with "file-roller" using synaptics and then just tried to install "file-roller" alone, the problem is still here. Then I thought it was a problem related to the HDD, so I went ahead and re-formated it using the EXT4 file system with no partitions. Re-booted and the problem is still here.
So, I decided to be humble and ask for help.

Whatever process I started with "file-roller" or one of its companion pkgs is still active somewhere, I believe is "alive" in the system's HDD, because it returns after a complete uninstall/reboot/install process.

I do not want to mess with "nautilus" itself, Do i need to uninstall/reinstall "nautillus-data" pkg?

I have run out of ideas, Please help me up! Thanks in advance!

Using:
System: Ubuntu 10.10, running solo in an EXT4 single partition.
Desktop: Gnome v2.32.0
Programs: file-roller v.2.32.0-0ununtu1; unzip v6.0-4; zip v3.0-3; xz-utils 4.999.9beta+20100527-1
USB HDD: 500GB, single partition, EXT4 file system.

---

### Post by oldos2er on 2011-03-09
Right-click a folder on your desktop (if there isn't one, create one), select Open with, other application, select File Browser and make sure "Remember the application..." is checked.

---

### Post by manerfiro on 2011-03-09
Thanks man!, Thanks so much, it worked, it worked! 

Now I can go back to my life.

Now... everything is working properly, but... is there an established process here in the forums to give you points or to report that you helped me to solve the issue? I would love to do that.

Well thanks for the help, if you have the time could you please tell me your opinion on what happened, so i can understand the problem better? If you do not have the time that's OK too. I am back to Linux heaven again!

---

### Post by oldos2er on 2011-03-09
> is there an established process here in the forums to give you points or to report that you helped me to solve the issue?

No, there used to be a 'Thanks' button, but it was removed because it was causing the forum database software some grief. A simple 'thank you' is more than enough, and you're welcome.  :)

> if you have the time could you please tell me your opinion on what happened, so i can understand the problem better? 

I don't pretend to understand it, I just know the solution because I've read it here many times already. It seems to be a general problem with 10.04 and 10.10; I don't know why (not a programmer). You'd need to ask a developer what's going on. Looks like it's already been reported as a bug: [https://bugs.launchpad.net/ubuntu/+bug/667071](https://bugs.launchpad.net/ubuntu/+bug/667071)

---

