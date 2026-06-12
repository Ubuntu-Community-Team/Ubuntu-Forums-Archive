---
title: "Unable to install software"
date: 2006-03-17
forum: General Help
---

### Post by calande on 2006-03-17
I am new to Kubuntu, and Linux in general, I haven't used Linux for years. I just installed Kubuntu, and things have changed, it's a nice piece of software, pretty polished :rolleyes:

I followed the [tutorial]("http://www.kubuntu.org/docs/kquickguide/C/ch02s07.html") to install software, but Adept doesn't seem to work...:confused:

Here's what happens: I click "System > Adept (Package Manager)", then it asks for my password (normal). Then it gives me an error message:

> Sorry - Adept
Could not find MIME type
application/octet-stream


Then I click "Ok", then I get another alert:

> Error - Adept
No MIME types installed.

I click "OK " again, and Adept shows up. So, here we go, I type "firefox" in the search field, and I get only one entry:

mozilla-firefox-locale-en-gb

Whis is reported to be already installed. But I want to install Firefox. If I type "firefox" in my terminal, it reports command not found.


Now let's try to install anything that is reported as "not installed". I select for instance "alien", and click "install package", then I click "Apply changes" and I get another message that I have no clue:

> Please insert the disc labeled 'Kubuntu 6.04_Dapper_Drake - Alpha i386 (20060217.2)' in the drive '/cdrom/' and press enter 

But I don't have such CD-ROM...:confused: 

Is it so hard to install software... Or am I missing something obvious :-k

---

### Post by invalid on 2006-03-17
I would suggest using synaptic to install software.
```
sudo synaptic
```

---

### Post by calande on 2006-03-17
Wow! Faster than you to reply: Impossible :)
Here's another problem:

> 
charles@ubuntu:~$ sudo synaptic
Password:
sudo: synaptic: command not found
charles@ubuntu:~$


---

### Post by bjweeks on 2006-03-17
[QUOTE=calande]Wow! Faster than you to reply: Impossible :)
Here's another problem:[/QUOTE]

synaptic is included in ubuntu not kubuntu...

---

### Post by bjweeks on 2006-03-17
o and to fix you problem you need to.

```
sudo gedit /etc/apt/sources.list
```

remove the first line of code that refers to the cd and save it. Try again.

---

### Post by invalid on 2006-03-17
[QUOTE=bjweeks]synaptic is included in ubuntu not kubuntu...[/QUOTE]
Ah ha, this is news to me. My apologies, please ignore my post.

---

### Post by MJN on 2006-03-17
Try **sudo apt-get install synaptic** *then* **sudo synaptic** (or find Synaptic in your K-menu under *System*).

Mathew

---

### Post by bjweeks on 2006-03-17
[QUOTE=MJN]Try **sudo apt-get install synaptic** *then* **sudo synaptic** (or find Synaptic in your K-menu under *System*).

Mathew[/QUOTE]

No, don't do this. You don't need synaptic you need to fix you sources.list

---

### Post by calande on 2006-03-17
[QUOTE=bjweeks]o and to fix you problem you need to.

```
sudo gedit /etc/apt/sources.list
```

remove the first line of code that refers to the cd and save it. Try again.[/QUOTE]


Thank you.

> 
charles@ubuntu:~$ sudo gedit /etc/apt/sources.list
Password:
sudo: gedit: command not found


I managed to remove that line though, but I still get the above error messages. Also, Adept doesn't seem to work when I click buttons...:confused:

---

### Post by calande on 2006-03-17
[QUOTE=MJN]Try **sudo apt-get install synaptic** *then* **sudo synaptic** (or find Synaptic in your K-menu under *System*).

Mathew[/QUOTE]

One more error message :( 

> charles@ubuntu:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package synaptic has no installation candidate
charles@ubuntu:~$

---

### Post by bjweeks on 2006-03-17
[QUOTE=calande]Thank you.



I managed to remove that line though, but I still get the above error messages. Also, Adept doesn't seem to work when I click buttons...:confused:[/QUOTE]

OMG sorry didn't see I was in the kubuntu forum

```
sudo kedit /etc/apt/sources.list
```

---

### Post by Jucato on 2006-03-17
Kedit is not installed by default in Kubuntu.
use Kate or Kwrite instead
```
sudo kate /etc/apt/sources.list
```

---

### Post by calande on 2006-03-17
Any idea? :(

---

### Post by bjweeks on 2006-03-17
[QUOTE=calande]Any idea? :([/QUOTE]

as he said
```
sudo kate /etc/apt/sources.list
```
or 
```
sudo nano /etc/apt/sources.list
```

---

### Post by aysiu on 2006-03-17
Use KWrite. *sudo* and Kate don't mix well.

Actually, just get a better sources.list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by MJN on 2006-03-17
[quote=bjweeks]No, don't do this. You don't need synaptic you need to fix you sources.list[/quote]

	 	 		Fair enough, I just couldn't see how  			 				'Sorry - Adept Could not find MIME type application/octet-stream' and 'Error - Adept No MIME types installed' were a sources issue and given the immaturity of Adept (and the multitude of problems that this is causing for some) I thought Synaptic might be a safer bet.

However, I bow to your better experience on this one... over to you Batman.

Mathew

---

### Post by aysiu on 2006-03-17
[QUOTE=MJN]Fair enough, I just couldn't see how  			 				'Sorry - Adept Could not find MIME type application/octet-stream' and 'Error - Adept No MIME types installed' were a sources issue and given the immaturity of Adept (and the multitude of problems that this is causing for some) I thought Synaptic might be a safer bet.[/QUOTE] Well, they're two separate issues. The most immediate is that Synaptic *cannot* be installed, and this appears to be because the sources.list is messed up.

Once the sources.list is fixed, we need to figure out whether apt-getting stuff is possible.

If that's possible, then we might be able to figure out what's wrong with Adept.

---

### Post by Jucato on 2006-03-17
oh, sudo and kate don't mix? Yeah I get some error messages but it still runs. But if you run kdesu kate, everything works perfectly (no error messages).

OT: Actually, I think we should try to change the habit of running GUI apps with sudo, whether from the command line or not. Here's the quote from the wiki:
> NEVER use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail. 

Back to the topic: Fix your sources.list as the previous posters have recommended. After that, run 
```
sudo apt-get update
```
(in Adept, click on Fetch Updates) and try to install something again.

---

### Post by calande on 2006-03-17
In the sources.list file, I removed the line refering to the CD-ROM. Then I launched Adept and I'm still getting the aforementioned error messages...

Clicking the "Fetch Updates" button has no effect...

---

### Post by Jucato on 2006-03-17
What error messages are you getting now? Still the MIME errors?
Can you also post your sources.list so we can take a look at it.

---

### Post by calande on 2006-03-17
Here it is:

```

# 
# deb cdrom:[Kubuntu 6.04 _Dapper Drake_ - Alpha i386 (20060217.2)]/ dapper main restricted 


# deb cdrom:[Kubuntu 6.04 _Dapper Drake_ - Alpha i386 (20060217.2)]/ dapper main restricted 

# Line commented out by installer because it failed to verify:
deb http://br.archive.ubuntu.com/ubuntu/ dapper main restricted 
# Line commented out by installer because it failed to verify:
deb-src http://br.archive.ubuntu.com/ubuntu/ dapper main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://br.archive.ubuntu.com/ubuntu/ dapper-updates main restricted 
# Line commented out by installer because it failed to verify:
deb-src http://br.archive.ubuntu.com/ubuntu/ dapper-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://br.archive.ubuntu.com/ubuntu/ dapper universe 
deb-src http://br.archive.ubuntu.com/ubuntu/ dapper universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://br.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 
deb-src http://br.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu dapper-security main restricted 
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted 
deb http://security.ubuntu.com/ubuntu dapper-security universe 
deb-src http://security.ubuntu.com/ubuntu dapper-security universe 

```

---

### Post by calande on 2006-03-17
As a side note, when I installed Kubuntu, I got a lot of warnings because the installer wasn't able to download packages from the Internet. This is due to the fact that I get connected to the Internet using PPPoE boadband, and my modem is not a router (bridge ADSL modem).

Maybe there is some more stuff missing to my system because of this. I got connected to the Internet after the system was fully installed.

---

### Post by Jucato on 2006-03-17
Your sources.list looks fine to me. But I see that you are running Dapper, which is still in development stage. So there's no guarantee that it will work 100% of the time. Have tried installing a more stable release, like Breezy Badger?

Also, you don't need an internet connection during installation. The installer will only attempt to detect networks and internet connection, but does not need it to install successfully.

---

### Post by MJN on 2006-03-18
Indeed.  The sources list is fine. Try the Dapper Drake forum - [http://www.ubuntuforums.org/forumdisplay.php?f=111]("http://www.ubuntuforums.org/forumdisplay.php?f=111") - you'll get the distro-specific help you need there.

(there are similar reports to yours in [http://www.ubuntuforums.org/showthread.php?t=139023]("http://www.ubuntuforums.org/showthread.php?t=139023&highlight=adept"))

Good luck!

Mathew

---

