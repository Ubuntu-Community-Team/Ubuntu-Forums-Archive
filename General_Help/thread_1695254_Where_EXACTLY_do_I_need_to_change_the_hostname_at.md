---
title: "Where EXACTLY do I need to change the hostname at?"
date: 2011-02-25
forum: General Help
---

### Post by Roasted on 2011-02-25
I know I can change the hostname in /etc/hostname, but where else is it critical to change? Reason I ask is there's a chance we might be introducing a few Ubuntu machines to our Windows network at work, and when it comes to re-naming them prior to adding them to the Windows domain, I want to make sure the process I'm using is accurate. Don't I have to change an entry in /etc/resolv.conf or something as well for things to mesh nicely with the rest of the environment?

---

### Post by seawolf167 on 2011-02-25
As far as I'm aware of the only two places to change it are

```
/etc/hosts
/etc/hostname
```

---

### Post by wyliecoyoteuk on 2011-02-25
You might also need to change it in smb.conf if you want it to show correctly in windows network neighborhood

---

### Post by Roasted on 2011-02-26
Is there some sort of utility that aids in efficiency with this or am I stuck having to change it manually in 3 places? Reason I ask is it's worse enough changing the name of hundreds of Windows computers. I don't want to add Ubuntu ones to the setup and, oh lol we gotta do triple the work... Granted I'm projecting less maintenance time in the long run versus the Windows systems, but still... just trying to be efficient.

---

### Post by amsterdamharu on 2011-02-26
> Is there some sort of utility that aids in efficiency with this or am I stuck having to change it manually in 3 places?
You don't have to do anything manually if you know how to bash script it you need to do it only once.
If you have to maintain many computers you can automate it with a bash script.


[http://www.cyberciti.biz/faq/unix-linux-replace-string-words-in-many-files/](http://www.cyberciti.biz/faq/unix-linux-replace-string-words-in-many-files/)
```
sed 's/old-name/new-name/g' /etc/hostname
sed 's/old-name/new-name/g' /etc/hosts
service hostname start

```

Now where to put the script and make sure it doesn't affect other stuff depends on your setup. Do you have to administrate a lot of Ubuntu computers?

---

### Post by amsterdamharu on 2011-02-26
As for automating it I think you could put something in /etc/init that will fetch script and execute it on startup or check every so often to see if there are administrative tasks to be performed.

Let's say you have /etc/init/adminjob.conf with the following content:

```
# adminjob - executes /usr/bin/adminscr.sh
#

description    "executes /usr/bin/adminscr.sh"

start on (starting network-manager
          or starting networking)

task
exec /usr/bin/adminscr.sh

```and /usr/bin/adminscr.sh
```

#!/bin/sh
tmp=`mktemp -q -d`
cd $tmp
wget http://myserver/admintasks/adminscript.sh
error=$?;
if [[ "$error" == "0" ]]
then
    bash adminscript.sh
fi
```Set the right permission to /usr/bin/adminscr.sh to be only read and executed by root.

There might be a problem that any user can see the adminscript so maybe you might replace it with a share that only root can access and remove the adminscript.sh after executing it.

Upstart has many events, here it is only executed when network-manager or networking is started but you might want to run it every time someone logs in.

There is also an option to use cron jobs

---

### Post by Roasted on 2011-02-26
> **amsterdamharu said:**
> You don't have to do anything manually if you know how to bash script it you need to do it only once.
If you have to maintain many computers you can automate it with a bash script.


[http://www.cyberciti.biz/faq/unix-linux-replace-string-words-in-many-files/](http://www.cyberciti.biz/faq/unix-linux-replace-string-words-in-many-files/)
```
sed 's/old-name/new-name/g' /etc/hostname
sed 's/old-name/new-name/g' /etc/hosts
service hostname start

```

Now where to put the script and make sure it doesn't affect other stuff depends on your setup. Do you have to administrate a lot of Ubuntu computers?

I'm not sure how many computers we are talking about. We are talking small scale to start with potential to expand, but as of now I'm predicting maybe 10 max. If things fly with amazing colors (which to be honest, I predict them to mesh rather nicely as long as I can figure out how to auto-add a folder on the desktop that links the user to their share on our Windows file server), then we may add more.

I wouldn't mind doing a little scripting. If there's a way to add a script to the Administrator desktop, for example, and somehow execute it in terminal with the computer name, that'd be sweet.

For example, let's say I have a script that will auto add whatever I type into the particular entries within those config files that need to be changed. Let's say the name of the script is namechange.

sudo namechange skynet

BAM - that system is named skynet. Reboot, blam done.

Is that what you're thinkin amsterdamharu?

---

### Post by amsterdamharu on 2011-02-26
My example shows a config file in /etc/init. This will be started whenever network is started so every time you start the computer.

The config will start a script in /usr/bin, you need to add that to every desktop. The general script will fetch a script from your webserver so that script you can change every time you need something done on the desktop(s). 
This webserver script could be real script file or could be a php file that takes parameters like computer name, ip address, user name, software installed and their versions, ...  
If you are more comfortable using php, .net or java you can put logic to the admin script here, so depending on computer name, user, software, hardware, ... you return different scripts.
According to those parameters the php could return a script.
(you can make it as complicated as you want)

When the /usr/bin script has fetched the admin script from the webserver it will execute it. Good thing is that the config files in /etc/init are executed on events like startup, login, network even key pressed like control + alt + delete  and they run as root so no reason for the user to be admin or have sudo rights.

The adminscript.sh could contain something like:
```
# read the current computer name
oldname=hostname;
newname=hostname;
# oldname and newname are the same now
if [ "$oldname" == "some name I want to change" ] then
newname = "the new name for 'some name I want to change'";
fi
# more if statements
sed -i "s/"${oldname}"/"${newname}"/g" /etc/hostname
sed -i "s/"${oldname}"/"${newname}"/g" /etc/hosts
service hostname start
```Because you added "service hostname start" there is no need to restart the computer, the new hostname is used after that command.

---

### Post by amsterdamharu on 2011-02-26
> how to auto-add a folder on the desktop that links the user to their share on our Windows file server
My bash scripting isn't up to par but your admin script (on your webserver) would look something like this:

```
#!/bin/sh
# create a link to Windows share on all users desktops (any user that logged on to this computer)
# it will create a link in every /home/user/Desktop folder but only if the file doesn't already exist
OIFS=$IFS; # save the internal seperator
IFS=$'\n';

for i in `find /home -maxdepth 1 -type d`; do 
    if [ -d "$i/Desktop" ]; then
        if [ ! -f "$i/Desktop/myshare.desktop" ]; then
            i="$i";
            myUser=$(echo ${i/\/home\//});
            myUser="$myUser";
            myShortcut="#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Link
Icon[en_US]=gnome-panel-launcher
Name[en_US]=myshare
URL=smb://myWindowsServerName/$myUser
Comment[en_US]=this is my share
Name=myshare
Comment=this is my share
Icon=/usr/share/icons/oxygen/48x48/emotes/face-laugh.png";
            echo "$myShortcut">"$i/Desktop/myshare.desktop";
            chown $myUser "$i/Desktop/myshare.desktop"
        fi
    fi
done

IFS=$OIFS;
# add hostname rename stuff here

```This script assumes a share with the same name as the user is on your server and your user's home directory has the name of the user login. So if you login to Ubuntu using peter, there is a directory /home/peter (the users home directory) and a windows share named peter.

---

