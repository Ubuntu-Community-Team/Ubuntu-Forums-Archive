---
title: "how can i upgrade thunderbird 3?"
date: 2009-12-08
forum: General Help
---

### Post by zhorks on 2009-12-08
currently using TB 2, wanting to upgrade TB 3

How can i do this upgrade?

Thanks

i grabbed the .tar.bz2 from the site. what do i do next?

---

### Post by scouser73 on 2009-12-08
**1 -** Extract the **.tar.bz2** file

**2 -** Enter **gksudo nautilus** in terminal

**3 -** Go to the folder **/opt**

**4 -** Copy & paste the Thunderbird file that you extracted to **/opt**

**5 -** Enter these commands into **Terminal** > **sudo -i**

*Enter your password if asked.*

> **cd /opt**
> **chown -R username filename**

[COLOR="Red"]**Obviously the username refers to you, and the filename to the file**[/COLOR]

**6** - Go to **System > Preferences > Main Menu**

**7** - In Main Menu, click on **New Item**

**8** - In the **Name** field enter **Mozilla Thunderbird Mail/News**

**9** - In the **Command** field enter **/opt/thunderbird/thunderbird**

**10** - In the **Comment** field enter **Mozilla Thunderbird Mail/News**

[[IMG]http://img121.imageshack.us/img121/7329/screenshot2c.png[/IMG]](http://img121.imageshack.us/img121/7329/screenshot2c.png/)

---

### Post by zhorks on 2009-12-08
thanks

---

### Post by e633 on 2009-12-08
Sorry but does this mean all my sensitive data will not be stored inside my _*encrypted*_ /home/myuser folder?

---

### Post by scouser73 on 2009-12-08
No, you only copy the Thunderbird folder [*which is the actual software*] to **/opt**, the Thunderbird profile and your emails will remain at **/home/username/.thunderbird**

---

### Post by e633 on 2009-12-08
Yup, thanks, i installed TB3 according to your instructions, started it with the --profileManager option then created a new user pointing to my old TB2 folder.

Needless to say migration was flawless, only the Enigmail extension needed an update!

---

### Post by danootz on 2009-12-08
Hey. How can I get an icon for the launcher for thunderbird? I've tried and I can't figure out how to do it.

---

### Post by fooey on 2009-12-08
> **e633 said:**
> ... started it with the --profileManager option then created a new user pointing to my old TB2 folder.

thx. :p

---

### Post by aysiu on 2009-12-08
Alternatively, you can use UbuntuZilla to install it:
[http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)

---

### Post by jfdm on 2009-12-09
Well the icons that i am using can be found in 

<install dir>/chrome/icons/default/

where install dir is where you placed thunderbird 3.0.

---

### Post by lariosa42 on 2009-12-09
scouser73 - 

I just wanted to say thank you for a very nice how to, done apparently on the spot, and with pictures!  Great job!

---

### Post by randomAccess on 2009-12-09
> **e633 said:**
> Yup, thanks, i installed TB3 according to your instructions, started it with the --profileManager option then created a new user pointing to my old TB2 folder.

Needless to say migration was flawless, only the Enigmail extension needed an update!

Hmmm, done it a zillion times, but this thunderbird simply does not recognise my old TH2 folder. I navigate it to the th2 folder and it still asks me to create a new mail account, etc. weird!

---

### Post by m3owner on 2010-01-01
(noob yesterday) I did the extraction and it came out with about 10 folders and 36 other files. exactly what am I to paste into the command line?

I'm trying to get T-bird, because Evolution wouldn't work with Yahoo POP. It is amazing that Mozilla just dumps T-bird to your Ubuntu desktop, whereas they walk you thru the Windows install. Ubuntu looks far too complex to do much. I've spent more time searching chat boards the last two days than in the last 2 years with XP issues.

---

### Post by nanotube on 2010-01-01
> **m3owner said:**
> (noob yesterday) I did the extraction and it came out with about 10 folders and a lot of other "stuff". exactly what am I to paste into the command line?

I'm trying to get T-bird, because Evolution wouldn't work with Yahoo POP. It is amazing that Mozilla just dumps T-bird to your Ubuntu desktop, whereas they walk you thru the Windows install. Ubuntu looks far too complex to do much. I've spent more time searching chat boards the last two days than in the last 2 years with XP issues.

just install it from the ubuntuzilla repository:

[http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)

---

### Post by m3owner on 2010-01-01
> **nanotube said:**
> just install it from the ubuntuzilla repository:

[http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)

I don/t understand since the Thunderbird link at your link above is the same source that got me to the 10 folders and 36 files I downloaded.

---

### Post by nanotube on 2010-01-01
> **m3owner said:**
> I don/t understand since the Thunderbird link at your link above is the same source that got me to the 10 folders and 36 files I downloaded.

er... don't know what you're talking about.

just follow the installation instructions on the ubuntuzilla site - add the repository, then apt-get install the thunderbird-mozilla-build package.

---

### Post by m3owner on 2010-01-01
uote=nanotube;8593568]er... don't know what you're talking about.

just follow the installation instructions on the ubuntuzilla site - add the repository, then apt-get install the thunderbird-mozilla-build package.[/quote]

I copied the first line beginning   "echo" all the way to "null"  even the part that had a blue duel ended arrow, into the command line after logging in. I got no response, the PC just sits there waiting for something else I guess.

any other ideas?

---

### Post by aysiu on 2010-01-01
> **m3owner said:**
> uote=nanotube;8593568]er... don't know what you're talking about.

just follow the installation instructions on the ubuntuzilla site - add the repository, then apt-get install the thunderbird-mozilla-build package.

I copied the first line beginning   "echo" all the way to "null"  even the part that had a blue duel ended arrow, into the command line after logging in. I got no response, the PC just sits there waiting for something else I guess.

any other ideas?[/QUOTE]
Can you paste the output of these commands? ```
cat /etc/apt/sources.list
sudo apt-get update
``` (P.S. Not sure if this is the problem, but after each command you paste, you have to hit the **Enter** key to have it take effect)

---

### Post by m3owner on 2010-01-01
> **aysiu said:**
> I copied the first line beginning   "echo" all the way to "null"  even the part that had a blue duel ended arrow, into the command line after logging in. I got no response, the PC just sits there waiting for something else I guess.

any other ideas?
Can you paste the output of these commands? ```
cat /etc/apt/sources.list
sudo apt-get update
``` (P.S. Not sure if this is the problem, but after each command you paste, you have to hit the **Enter** key to have it take effect)[/quote]

This is what I got from your code:

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main
deb [http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main
deb [http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main
david@lindalaptop:~$ sudo apt-get update

---

### Post by m3owner on 2010-01-01
I had hit enter after I copied the link from the site given in 18 above, but as far as I can tell it did nothing as I didn't get any indication it completed the task.

The "dump" I got in 19 above means nothing to me. I am not a coder, just a PC user that is trying to see if Linux (Ubuntu) is a viable alternative for me. So far is sure seems like I need to be a programmer, and I decided many years ago that I don't want to be more than an educated user.

---

### Post by aysiu on 2010-01-01
> **m3owner said:**
> 
```
[noparse]deb http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
deb http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
deb http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt all main[/noparse]
``` It looks as if you added the UbuntuZilla repository three times. You need to delete two of those.

**Step 1**
Go to System > Administration > Software Sources and enter your password if prompted

**Step 2**
Click the *Other Software* tab

**Step 3**
Delete two of the *[noparse]http://switch.dl.sourceforget[/noparse]...* entries. _Make sure one entry still remains_

**Step 4**
Click *Close* and then *Reload* when prompted

**Step 5**
Go to System > Administration > Synaptic Package Manager and use Synaptic to install *thunderbird-mozilla-build*

If you don't know how to use Synaptic to install software, then read this:
[http://www.psychocats.net/ubuntu/installingsoftware#synaptic](http://www.psychocats.net/ubuntu/installingsoftware#synaptic)

---

### Post by m3owner on 2010-01-01
After step 4, Close and reload, I got the following error:

W: GPG error: [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29

I had entered my password properly when prompted and did leave one of the required code lines in place.

I've been trying to load T-bird because Evolution will not connect to my Yahoo e-mail account because Yahoo apparently does not accept POP access. 

If I can get over the error above, I'll try to install T-bird using the Synaptic software. I just read the tutorial and I hope I don't have to choose multiple files and make all the other choices the tutorial gives. I have little bisis to make the choices.

Thanks for trying to help (two days trying to get access to Yahoo Mail thru the Ubuntu desktop).

This sure is not like Windows, where you download and run new programs.

---

### Post by aysiu on 2010-01-01
Yeah, you should add the signing key by pasting this command into the terminal ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
```

---

### Post by m3owner on 2010-01-01
I opened a new terminal and pasted in your code after my login, hit enter and got the following:

david@lindalaptop:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
[sudo] password for david: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com C1289A29
gpg: requesting key C1289A29 from hkp server keyserver.ubuntu.com
gpg: key C1289A29: public key "Daniel Folkinshteyn (Ubuntuzilla signing key) <nanotube@users.sourceforge.net>" imported
gpg: Total number processed: 1
gpg:               imported: 1
david@lindalaptop:~$ 

I then went into the software sources, highlighted the T-bird related line, hit close, and nothing happened. It did not come back and ask me to reload it. Just for your info, being a noob, none of this process really makes any sense to me, so I am just trying to follow directions.

---

### Post by aysiu on 2010-01-01
That all sounds good. It shouldn't ask to reload, because you haven't changed your sources, only added the signing key.

Go ahead and use Synaptic to install *thunderbird-mozilla-build*. Afterwards, I can explain to you what you just did.

---

### Post by sports fan Matt on 2010-01-01
I just tried to add that repository and got ailed to fetch [http://switch.dl.sourceforge.net/pro...la/mozilla/apt/dists/all/main/binary-i386/Packages.gz](http://switch.dl.sourceforge.net/pro...la/mozilla/apt/dists/all/main/binary-i386/Packages.gz)  404  Not Found [IP: 130.59.138.21 80]
Some index files failed to download, they have been ignored, or old ones used instead.

Running karmic for now.

---

### Post by m3owner on 2010-01-01
Thunderbird installed and I was able to open it and work on the configuration to access my Yahoo account, but it came back and said that either my access name of password is wrong. I went thru very carefully and reentered my Yahoo account name and my Yahoo password, but the same result.  

Is it looking for some other password (my Ubuntu password?) or 1.) do I now need to get more programs to access Yahoo or 2.) have the same problem that I had with Evolution, which is that Yahoo won't allow POP access by other programs?

When I was going thru the install program, it told me that the authenticity of the program couldn't be verified and that I could be installing an unsecure application. I thought that was strange for an Ap directly from Mozilla ( it was Thunderbird-mozilla build)

I found this link:  [http://webmail.mozdev.org/installation.html](http://webmail.mozdev.org/installation.html)

and wonder if I need to download the web mail and Yahoo components. If I do, I'll need to know the procedure because my first attempt to download from Mozilla was apparently not the right way.

---

### Post by jasonsjunk on 2010-01-01
As I recall Yahoo only allows POP access to their premium (paid) e-mail accounts.  The only Yahoo e-mail that allows POP3 access is their Yahoo Mail Plus e-mail.

---

### Post by m3owner on 2010-01-01
Hopefully there are ways for me to access my Yahoo e-mail account thru a Ubuntu e-mail program.

wnelson on the Evolution chat site of the forums, suggested that T-bird with the webmail/yahoo extensions would work. I now have T-bird installed and need help doing the webmail/yahoo extensions.

I'm 10 hours and 2 e-mail programs in so far.

---

### Post by m3owner on 2010-01-02
Any help out there for the issues listed in #27 above?

---

### Post by nanotube on 2010-01-03
> **sox fan Matt said:**
> I just tried to add that repository and got ailed to fetch [http://switch.dl.sourceforge.net/pro...la/mozilla/apt/dists/all/main/binary-i386/Packages.gz](http://switch.dl.sourceforge.net/pro...la/mozilla/apt/dists/all/main/binary-i386/Packages.gz)  404  Not Found [IP: 130.59.138.21 80]
Some index files failed to download, they have been ignored, or old ones used instead.

Running karmic for now.

the repo works fine for me... give it another try - sourceforge was having some occasional network problems in the past couple of days...

---

### Post by m3owner on 2010-01-03
> **nanotube said:**
> the repo works fine for me... give it another try - sourceforge was having some occasional network problems in the past couple of days...

Thanks for your reply. I recognize your name, nanotube, and know you've helped many before on this forum..

I'm a noob. If you look at the responses to my prior postings, you will see the detail it took for me to get T-bird installed.

Repo, karmic, etc don't mean anything to me. With Windows, you just download and run. With Linux, it seems there is a lot of copy/paste if you know what to copy and where to paste. I don't. Little things like instructions to use a Command line where the Linux app is called Terminal mislead me. 

I've got T-bird 3 and the link for the webmail& yahoo plugin are listed for 2.1, so maybe that is the problem.

It looks like if this doesn't work then the only e-mail I will have is getting Yahoo thru the Firefox browser. If that is all Linux can do, then the experiment will have been short-lived.

---

### Post by nanotube on 2010-01-03
> **m3owner said:**
> ...yahoomail ...

have you tried setting your account up as per these instructions:
[http://techblissonline.com/yahoo-pop3-and-smtp-settings/](http://techblissonline.com/yahoo-pop3-and-smtp-settings/)

note carefully the server and port settings, and note also that you need to 'enable pop access' for your yahoo account through the yahoo webmail interface. 

(were you able to access your yahoo mail account through some local client under windows? if so, use those exact same settings that worked before)

---

### Post by m3owner on 2010-01-03
In yahoo classic, when I choose POP and Forwarding, the only choice is "Upgrade to Mail Plus" and account you have to pay for. Not for me. I guess this option doesn't help.

How about the install process for webmail/Yahoo plugins referenced above?

---

### Post by nanotube on 2010-01-03
> **m3owner said:**
> In yahoo classic, when I choose POP and Forwarding, the only choice is "Upgrade to Mail Plus" and account you have to pay for. Not for me. I guess this option doesn't help.


well, in that case, you're out of luck, as far as pop access goes. 

> 
How about the install process for webmail/Yahoo plugins referenced above?

the webmail extension home is here:
[http://webmail.mozdev.org/installation.html](http://webmail.mozdev.org/installation.html)

apparently it has not yet been ported to tb3. 


overall, here's what i would suggest:

1) install thunderbird 2 and the webmail extension. 
2) suck off all your mail from yahoo to your local disk
3) sign up for a gmail account (or any other provider that does give free pop access)
4) start using gmail (or whatever else you choose) and drop yahoo. any provider that locks you in is just not worth it these days.

---

### Post by m3owner on 2010-01-03
I guess I'll wait for the webmail/yahoo plugin to come out for TB3 and just access my Yahoo mail thru my browser. It took about 6 hours of coaching to get TB3 installed. I thought wnelson had been able to do it for TB3, but I got no response confirming it or getting directions.

Thanks again for trying.

---

### Post by nanotube on 2010-01-03
> **m3owner said:**
> I guess I'll wait for the webmail/yahoo plugin to come out for TB3 and just access my Yahoo mail thru my browser. It took about 6 hours of coaching to get TB3 installed. I thought wnelson had been able to do it for TB3, but I got no response confirming it or getting directions.

Thanks again for trying.

well, if you have no pop access enabled on your account, then regardless of which email client you try, it will not work. no other way around it.

so... you have two choices: either uninstall tb3 and use tb2 + webmail addon (the webmail addon essentially just parses the browser interface to get your mail), or just use the web browser.

---

### Post by nanotube on 2010-01-06
new news for you, m3owner:

see post #3 in this thread, for how to enable pop access on yahoo mail for free (switch to 'asia' locale):
[http://ubuntuforums.org/showthread.php?t=1372937&highlight=thunderbird](http://ubuntuforums.org/showthread.php?t=1372937&highlight=thunderbird)

---

### Post by dawurz on 2010-01-09
Posting info that worked for me found here: 
[http://www.patrickmicka.com/uncategorized/mozilla-thunderbird-3/](http://www.patrickmicka.com/uncategorized/mozilla-thunderbird-3/)

Next, open a terminal and enter the following two commands to extract the archive you just downloaded:[INDENT]cd ~/Desktop (change to the folder that contains the thunderbird tar, Patrick is presuming it is the desktop here - dawurz)
tar xfvj thunderbird-3.0.tar.bz2
[/INDENT]You don&#8217;t need the original archive any longer, so delete with the following command (this is optional of course - dawurz):[INDENT]rm ~/Desktop/thunderbird-3.0.tar.bz2
[/INDENT]After you&#8217;ve unpacked the archive enter the following command to move it to a more convenient location:[INDENT]sudo mv ./thunderbird /opt/
[/INDENT]Everything should be in order now, so let&#8217;s move to the directory and make sure it works:[INDENT]cd /opt/thunderbird/
[/INDENT]Finally, run the following command to launch Thunderbird:[INDENT]./thunderbird
[/INDENT]The link to Patrick's site also contains easy directions for creating a shortcut.  Finding your way to the Thunderbird icons shouldn't be hard, they're in /opt/thunderbird/chrome/icons/default

Finally, if you tried it the way that will alter your existing Firefox install to the development version, you can remove the mozilla daily ppa by doing this:

Note: the PPA in this post also has some Firefox daily builds (and further "Shredder" daily builds) so if you don't wish to use these, simply remove the ubuntu-mozilla-daily PPA after installing Thunderbird. To do this, go to System > Administration > Software Sources, on the second tab called "Other software", look for "[http://ppa.launchpad.net/ubuntu-mozilla-daily/](http://ppa.launchpad.net/ubuntu-mozilla-daily/)..." and uncheck it. (NOTE: You can also select REMOVE. - dawurz)

found here: [http://www.facebook.com/note.php?note_id=197656644742](http://www.facebook.com/note.php?note_id=197656644742)

---

### Post by jimmyUT on 2010-01-14
OK, so I am a newbie to Ubuntu and Linux and have decided to to give windows XP the boot.

I love TB 3 but am having trouble installing.  

                **Re: how can i upgrade thunderbird 3?**                                                                                  **1 -** Extract the **.tar/bz2** file

             **2 -** Enter **gksudo nautilus** in terminal

             **3 -** Go to the folder **/opt**

             **4 -** Copy & paste the Thunderbird file that you extracted to **/opt**

              **5 -** Enter these commands into **Terminal**      Quote:
                                                 **sudo -i**                                 
                 *Enter your password if asked.*

                Quote:
                                                 **cd /opt**                                 
                Quote:
                                                 **chown -R username filename**


I got to this part and am wondering what I use as my username and what is the filename????  is it my username that I log into Ubuntu with?

and what file name... There are a lot of files in the thunderbird folder I extracted.

Thanks in advance for your help.

---

### Post by scouser73 on 2010-01-14
> **jimmyUT said:**
> OK, so I am a newbie to Ubuntu and Linux and have decided to to give windows XP the boot.

I love TB 3 but am having trouble installing.  

                **Re: how can i upgrade thunderbird 3?**                                                                                  **1 -** Extract the **.tar/bz2** file

             **2 -** Enter **gksudo nautilus** in terminal

             **3 -** Go to the folder **/opt**

             **4 -** Copy & paste the Thunderbird file that you extracted to **/opt**

              **5 -** Enter these commands into **Terminal**      Quote:
                                                 **sudo -i**                                 
                 *Enter your password if asked.*

                Quote:
                                                 **cd /opt**                                 
                Quote:
                                                 **chown -R username filename**


I got to this part and am wondering what I use as my username and what is the filename????  is it my username that I log into Ubuntu with?

and what file name... There are a lot of files in the thunderbird folder I extracted.

Thanks in advance for your help.


Use the name that you sign into Ubuntu with and the filename will be thunderbird

---

### Post by nanotube on 2010-01-14
> **jimmyUT said:**
> OK, so I am a newbie to Ubuntu and Linux and have decided to to give windows XP the boot.

I love TB 3 but am having trouble installing.  

                **Re: how can i upgrade thunderbird 3?**                                                                                  **1 -** Extract the **.tar/bz2** file

             **2 -** Enter **gksudo nautilus** in terminal

             **3 -** Go to the folder **/opt**

             **4 -** Copy & paste the Thunderbird file that you extracted to **/opt**

              **5 -** Enter these commands into **Terminal**      Quote:
                                                 **sudo -i**                                 
                 *Enter your password if asked.*

                Quote:
                                                 **cd /opt**                                 
                Quote:
                                                 **chown -R username filename**


I got to this part and am wondering what I use as my username and what is the filename????  is it my username that I log into Ubuntu with?

and what file name... There are a lot of files in the thunderbird folder I extracted.

Thanks in advance for your help.

if you're a newbie, it's easiest to use a repository to install software. if you're running 32bit ubuntu, you can use the ubuntuzilla repository which contains the latest mozilla releases.
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by jimmyUT on 2010-01-15
So I tried again... now when i put in

gksudo nautilus in the terminal i get

[I]GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
[/I]

any ideas for a newbie that doesn't understand ubuntu yet?  I would just stick with 2.0 for now, but it won't show subject or sender  unless i click on that particular email which is really annoying

---

### Post by jimmyUT on 2010-01-15
OK, scratch last post.  I have TB3 installed and working properly.

The icon is not there though.  I downloaded the thunderbird.png icon file and have it in my downloads.  When I try to move it to the icons folder it says I don't have permission.  How do I get it in there ?? 

Thanks again for all the help.

---

