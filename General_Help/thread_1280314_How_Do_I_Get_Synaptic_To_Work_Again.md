---
title: "How Do I Get Synaptic To Work Again?"
date: 2009-10-01
forum: General Help
---

### Post by Spaceman9 on 2009-10-01
I tried installing OpenOffice into UbuntuStudio 9.04.and it didn't install OpenOffice completly. Now Synaptic is messed up. When I run Synaptic it gives this error message:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried running sudo dpkg --configure -a and it tries to finish installing OpenOffice, but can't finish installing it. 

Is there anything I can type into a terminal to get Synaptic working again???

Thanks for any help.

---

### Post by vishy1618 on 2009-10-01
Try 

sudo apt-get install -f

That should do it. Also, make sure you have an active internet connection. BTW, what is the error message when the open office installation fails?

---

### Post by Bucky Ball on 2009-10-01
. 

Posted in error

---

### Post by Spaceman9 on 2009-10-02
I'd like to show you what happens in the terminal but when I run any other app with the terminal my computer locks up.

I tried sudo apt-get install -f and I got this:

bruce@ubuntu-mine:~$ sudo apt-get install -f
[sudo] password for bruce: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
bruce@ubuntu-mine:~$ 

Is there any other command I can run???


I was thinking if this is happening because of a bug in the rt kernel may be I could install a different kernel, install OpenOffice and then reinstall the rt kernel. Or, may be I could just install OpenArtist. It's based on Ubuntu.

---

### Post by Spaceman9 on 2009-10-03
OK, this is driving me nuts. I've looked at the stuff in the documentation at Ubuntu about Synaptic. I looked at the Synaptic site for help but there's nothing there. There must be a command I could type into a terminal to get it working again. I don't want to have to reinstall UbuntuStudio if the problem can be solved with a simple command.

Is anybody here an expert about Synaptic????

---

### Post by Bucky Ball on 2009-10-04
Try post #2 here and let us know. 

[http://ubuntuforums.org/showthread.php?t=388348](http://ubuntuforums.org/showthread.php?t=388348)

The command it is asking for seems to need:

```
sudo apt-get update
sudo apt-get upgrade
```... straight after you've performed the command. See if it works.

---

### Post by Spaceman9 on 2009-10-04
Ok, I looked at the link and typed in sudo

apt-get update

and then typed in 

sudo apt-get upgrade

With each one I got the message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

In a different thread I found this:

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoremove

I'm going to try this starting with "sudo apt-get --fix-missing install" and I'll post the results.


UPDATE:
Ok, so I ran those commands and kept getting "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem".

While I was trying those commands the Update Manager popped up and I exited the terminal and tried to run the Update Manager. It's just sitting there not doing anything. It all seems to be caused by a problem with the rt kernel and openoffice...I think.

---

### Post by danwood76 on 2009-10-04
What are the errros from:
```

sudo dpkg --configure -a

```
?
That will point you in the right direction.

---

### Post by Spaceman9 on 2009-10-04
I grt the error with "sudo dpkg --configure -a" too. I get the error with everything I type.

---

### Post by Bucky Ball on 2009-10-04
This sequence as described on the link earlier:

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Spaceman9 on 2009-10-04
> **Bucky Ball said:**
> This sequence as described on the link earlier:

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

I still get the same error message "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."

I tried "sudo apt-get install openoffice" and it started but stopped at openoffice.org-emailmerge.

Is there anyway to install a different package manager?

---

### Post by Bucky Ball on 2009-10-04
The package manager is not your problem. You would get the same error even if there was another.

---

### Post by blueridgedog on 2009-10-04
I have used these commands to move a stuck update process:

```
sudo dpkg --configure -a
sudo aptitude -f install
sudo aptitude dist-upgrade
```

---

### Post by Spaceman9 on 2009-10-04
> **blueridgedog said:**
> I have used these commands to move a stuck update process:

```
sudo dpkg --configure -a
sudo aptitude -f install
sudo aptitude dist-upgrade
```


I've tried all of that but it doesn't fix the problem. It seems to be a problem with installing openoffice into ubuntu studio.

---

### Post by espenlur on 2009-10-04
I had the same problems with the Java-package: dpkg mess up and system freeze. Should I use the autoremove command or try to remove / reinstall / downgrade the dpkg?

---

### Post by fooman on 2009-10-04
are you giving Oo ample time to install/update?

i had some updates the other day on one of my machines that had not been updated (or even turned on) for ages... and it seemed as if the openoffice update took a REALLY long time.  in fact,  i just left it running and ran out for awhile.  when i came home later...it was finished.  i have no idea how long it ended up taking.

that was around the same time as the beta release...so i figured the servers were tied up with that.

my suggestion:  run "sudo dpkg --configure -a" again and when you get to the openoffice update that seems to hang....let it run.

---

### Post by Spaceman9 on 2009-10-04
fooman I always give things whatever time they need to do whatever they need to do. I do a lot of work with 2D and now 3D graphics and some of that takes hours to finish doing things. This problem seems to be caused by a problem with the rt kernel and openoffice. There are other threads about the same problem.

PCLOS Gnome had a problem with installing openoffice for a short time but they fixed it. PCLOS 2009 doesn't have an rt kernel thought so I don't know what the problem was there.

My first computer was a commodore 64 that I bought in 1983 for $200.00. I have to laugh when I think about that computer. $299.00 today will get you a netbook that's way more powerful then a 64 was.

So I started working with computers in DOS in 1983 then Windows 3.1 in 1994 and now Linux in 2007. So I know you're right that computers need time to do their thing but I've been waiting for around a year for the Ubuntu team to get the shutdown sound working again and now there's this thing with installing openoffice.

---

### Post by Bucky Ball on 2009-10-04
To be honest I run the rt kernel and openoffice installed easy peasy, no problem, and has been rock solid for a few months now so not sure what is going on for you. Never heard any problems with OOffice and the rt kernel. Find it hard to imagine why there would be but guess it depends on the circumstances. Maybe I was lucky.

---

### Post by Spaceman9 on 2009-10-05
May be you are lucky or may be you know what you're doing. It looks like the only fix is to reinstall so as long as I have to reinstall I might as well try MEPIS and OpenSUSE.

---

