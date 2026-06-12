---
title: "Writing a script to automatically change computer name?"
date: 2011-04-06
forum: General Help
---

### Post by Roasted on 2011-04-06
In order to effectively change the computer name of an Ubuntu system, I've been told I need to edit /etc/hosts and /etc/hostname.

Is there a way I can set up a script that I have on the administrator desktop, and just double click it and put in the computer name I want to change it to, and it save hosts + hostname and then reboot the system?

---

### Post by blueridgedog on 2011-04-06
You could conceivably write a bash script that took a host name as a command line argument, then wrote a hosts and hostname file in a temporary directory, then used sftp to push the files to the remote system, if you had credentials to get to the system and did not object to using sftp as root (with root enabled on the remote system).  The same script could use ssh to connect and issue a restart command.  Others may have better ways to break it apart.

---

### Post by Roasted on 2011-04-06
Hmm, let's break it down like this. Let's say the script is called rename, and it's executeable and sitting on the desktop.

So I launch terminal, CD to Desktop, and run "rename library-00"

Thereby taking library-00 as the new computer name in /etc/hostname and thereby replacing all previous entries of the computer name in /etc/hosts.

If it doesn't auto reboot, it's fine. The rename is the key. Can it be done? If so, I'm curious if someone could help me construct the script... after all, if I already knew how to do it, it'd be done already. :guitar:

---

### Post by Cheesehead on 2011-04-06
It really depends on what you want to accomplish with the rename.

These are the commands your script will need:
1) When your system boots, the script /etc/init/hostname.conf tells the system what it's name is. It's a really easy script:```
hostname -b -F /etc/hostname   # Requires root or sudo

```So you can do the same thing at any time because *hostname* is a command:```
hostname MyNewSystemName
```
2) You won't need to reboot, but you may need to restart your X server.
3) If this system is on a network will may need to substitute the hostname in /etc/hosts. Awk or sed are very good for simple substitution like this:
```

cat /etc/hosts | sed s/oldname/newname/ > /tmp/newhosts
mv /tmp/newhosts /etc/hosts

```

Now use a bit of logic to make it all work. The following isn't a complete product, but shows you how it all fits together. It could make a good starting point for your script.
```

#WARNING - THIS IS UNTESTED AND MIGHT REALLY HOSE YOUR SYSTEM.
#You got it for free off the internet. You have been warned.

oldname=$(cat /etc/hostname)
newname=$1

# You'll need to test that the new name exists here, and exit gracefully if it does not.

hostname "$newname"
echo "Hostname changed from $oldname to $newname"

cat /etc/hosts | sed s/"$oldname"/"$newname"/ > /tmp/newhosts
mv /tmp/newhosts /etc/hosts
echo "The /etc/hosts file has been changed"

echo "Don't forget to logout and log back in before your X server crashes..."

```

---

