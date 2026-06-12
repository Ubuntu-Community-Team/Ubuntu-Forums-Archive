---
title: "Script with su asks for password at boot"
date: 2009-08-23
forum: General Help
---

### Post by slamhound on 2009-08-23
I have a Jaunty box that I use as a headless server (though I run the desktop version) to run Squeezecenter.  Everything works fine except one thing.  I integrate MusicIP with Squeezecenter and to get it to work properly, MusicIP needs to start up on boot before SC.  I followed the how-to on the SC wiki:
 

 [http://wiki.slimdevices.com/index.php/Integrating_MusicIP_with_SqueezeCenter](http://wiki.slimdevices.com/index.php/Integrating_MusicIP_with_SqueezeCenter)
 

 The main thing is to put a script (called mmserver) into /etc/init.d/ and then use BUM to make sure it starts up before SC (you have to fill in the username and path to the MusicIP folder in the script below).  Here is the script:
 

 #! /bin/sh 
# NON-PRIVIELEGED USER TO RUN MUSICMAGICSERVER. USER= 
# PATH TO THE MUSICMAGICMIXERSERVER  
export MUSICHOME= 
case $1 in
start) 
        su - $USER -c $MUSICHOME"MusicMagicServer start  & > /dev/null" 
         echo "Running MusicMagicServer"         exit         ;;     
stop) 
        su - $USER -c $MUSICHOME"MusicMagicServer stop  & > /dev/null" 
         echo "Stopped MusicMagicServer"         
exit         ;; 
    *)         echo "Usage: /etc/rc.d/init.d/mmserver { start | stop }"         exit         ;; 
esac 

I did all this, but MusicIP does not start automatically.  I think the problem is that when the script runs, it requests a password.  For instance, if I just run &#8220;/etc/init.d/mmserver start&#8221; from a command line, it asks me for a password (even though I'm not running it with sudo).  I assume that when it runs at boot, it doesn't get the password that it needs, so it doesn't start.   
 

 Can anyone see what is wrong with this script so that it is making this ask for a password?  I assume it has something to do with the way that it is using su, but this is all pretty new to me, and the script is identical to what many others with SC and MusicIP seem to be using successfully.

---

### Post by aysiu on 2009-08-24
It's trying to switch to a non-root user.

I don't think that's necessary.

If it's in /etc/init.d it should be run with root privileges already.

---

### Post by DaithiF on 2009-08-24
Hi, maybe its just a copy/paste error when you posted the script here, but as posted this part is incorrect:
```
# NON-PRIVIELEGED USER TO RUN MUSICMAGICSERVER. USER= 
# PATH TO THE MUSICMAGICMIXERSERVER  
export MUSICHOME= 

```
The USER=   part should be on its own line, not on the same line as the # comment above, (and you should have your username filled in).

As aysiu says, I'm not really sure why it wants to run as a particular user rather than as root, but assuming theres a good reason for that, then fixing the part above will at least give you a valid user for su -c to switch to.

---

### Post by slamhound on 2009-08-24
Sorry about that.  That came from my inexperience in posting to these forums. The line breaks from the script did not get carried over correctly in my post, but they are correct in the script itself.  The USER statement is on its own line in the script and I have filled in the USER (along with the path to the directory after MUSICHOME).  

So the script works properly, but it just asks for the password, which is the problem.  

Again, the script is from MusicIP; it comes with the program and just needs to be edited to get it to work.  I've posted to the SC forums, and it doesn't seem like others are having the problem that I am having, even though MusicIP is pretty widely used by SC users (and therefore, this script must be widely used).  And the MusicIP forum has been taken down because MusicIP is pretty much dead.  So I figured I'd post here, as this seems like more of a script problem than a specific MusicIP problem.

Anyone have any ideas about why it would be using su in this context when it should already be running as root?

---

### Post by DaithiF on 2009-08-24
ok.  so lets break it down into small pieces:  this script is going to get run as root, and 
```
su - someuser -c somecommand
``` 
should not require a password, because root has the ability to su to anybody without requiring a password.

so what happens if you :
1. switch to root interactively:
```
sudo -i
```
2. and then run:
```
su - yourusername -c /path/to/musicmagicwhatever start  &

```?

---

### Post by slamhound on 2009-08-24
[FONT=Verdana]Thanks.  This sort of trouble-shooting advice is very helpful. Here's what I did (and I correctly replaced “path to” with the actual path and the “user” with my username):

[/FONT]   [FONT=Verdana]If I sudo -i

[/FONT]    [FONT=Verdana]and then

[/FONT]    [FONT=Verdana]su - <user> -c /path/to/MusicMagicServer start 
[/FONT]   [FONT=Verdana]or 
[/FONT]   [FONT=Verdana]su - <user> -c /path/to/MusicMagicServer start & > /dev/null”

[/FONT]    [FONT=Verdana](I'm not sure what the “& > /dev/null” does and whether it is needed)

[/FONT]    [FONT=Verdana]I get:

[/FONT]    [FONT=Verdana]# MusicIP Server 1.8 
[/FONT]  [FONT=Verdana]Copyright (C) 2006-2007 MusicIP Corporation 
[/FONT]  [FONT=Verdana]Usage: MusicIPServer [options] start 
[/FONT]         [FONT=Verdana]MusicIPServer stop 
[/FONT]  [FONT=Verdana]Options: 
[/FONT]      [FONT=Verdana]-help              Show help message 
[/FONT]      [FONT=Verdana]-verbose           Log verbose info 
[/FONT]  [FONT=Verdana]For more docs, see [http://mixer.musicip.com/server](http://mixer.musicip.com/server)

[/FONT]    [FONT=Verdana]This is strange, because I do not get this message when I just run the script with a password and I haven't seen the command “MusicIPServer” anywhere (and running MusicIPServer start from a command line does nothing).

[/FONT]    [FONT=Verdana]I also tried to troubleshoot just by running:

 “/path/to/[/FONT]  [FONT=Verdana]MusicMagicServer start & > /dev/null” from a command line and it worked fine (i.e., the server starts) without asking for a password.

[/FONT]    [FONT=Verdana]So to summarize, just running the MusicMagicServer start command works with no password.  Using sudo -i and running the su – user -c command gets a message that I haven't seen before (but no password request) and that is different than the outcome of running the same command without the su – user -c at the beginning or running the script with a password.

[/FONT]    [FONT=Verdana]I also tried editing the script to get rid of the su – user -c and just leaving the command.  When I run the script from command line, it works with no password prompt.  However, it still doesn't run at startup; so perhaps getting it to run at startup is a different problem.[/FONT]

---

### Post by Mister.Vash on 2009-08-25
Your 'export MUSICHOME', does it have the trailing slash as show at the bottom? /path/to/music wouldn't work, but /path/to/music should (obviously replacing that with the location that the MusicMagicServer file is location in - change it if it isn't like that)

Once you've verified the line, run:
sudo /etc/init.d/mmserver start 
and see if that does it - it should only prompt you for the sudo password, you shouldn't be prompt for the su passwords

If that works then take a look a the settings in boot up manager and make sure it is active


```
#! /bin/sh
# NON-PRIVIELEGED USER TO RUN MUSICMAGICSERVER. 
USER=username
# PATH TO THE MUSICMAGICMIXERSERVER
export MUSICHOME=**[COLOR="Red"]/path/to/music/[/COLOR]**
case $1 in
start)
su - $USER -c $MUSICHOME"MusicMagicServer start & > /dev/null"
echo "Running MusicMagicServer" exit ;;
stop)
su - $USER -c $MUSICHOME"MusicMagicServer stop & > /dev/null"
echo "Stopped MusicMagicServer"
exit ;;
*) echo "Usage: /etc/rc.d/init.d/mmserver { start | stop }" exit ;;
esac 


```

---

### Post by slamhound on 2009-08-25
Okay, so after reading responses here and on the squeezecenter forum, I am now thinking that perhaps the password is not the problem.  If I have this correct, anything in init.d that is run at startup will be run as root. The su - user -c will run mmserver as a nonprivileged user rather than running as root (and I have verified that just running the command within the script can be run without a password).  And, as mister.vash suggested, using sudo before the script results in a request for the sudo password, but not a password from the script.  Also, changing the line within the script to remove the su starts the program if I run the script from command line, but it still doesn't start up at boot. 

So the problem must be with the way the script is running at boot.  I have tried it two ways.  The first was using BUM.  The service was marked as "activated" and the priorities were what I wanted them to be.  I also used BUM to deactivate it and I tried using update-rc.d.  Both ways created the appropriate symlinks in the appropriate folders, but neither way got mmserver to start at boot.  

People on the squeezecenter suggested creating and adding a line to an /etc/rc.local file.  But in reading up on this it seems that this is not the preferred way to do things in ubuntu. Is that correct?

Is there any log that records what happens when the scripts in init.d are run so I can troubleshoot what is happening here?

---

