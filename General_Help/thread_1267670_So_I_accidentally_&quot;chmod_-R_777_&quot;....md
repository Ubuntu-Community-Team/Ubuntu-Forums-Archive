---
title: "So I accidentally &quot;chmod -R 777 /&quot;..."
date: 2009-09-16
forum: General Help
---

### Post by Cheesejaguar on 2009-09-16
So I was debugging something on my server and it kept giving me the error that it didn't have necessary access to a file but wouldn't tell me which file it was having problems with.  I got frustrated so I just executed "sudo chmod -R 777 /".   Needless to say this has done all sorts of nasty things to my computer.  Nothing will run, SSH will not connect, etc.  

Is there any way to repair this stupid mistake?

---

### Post by Rhubarb on 2009-09-16
ouch.

I don't have much experience in this particular case, but I recommend you get physical access to the server, and back it all up.
Then re-install everything and copy documents / websites etc back from your backup with the correct permissions.

Other than that, I can't think of any other ways that'll help to undo your predicament.  (aside from booting from a live CD and changing the permissions manually).

---

### Post by Cheesejaguar on 2009-09-16
I'm guessing there are a lot of files to be changed? I guess I'll just try to copy everything off the OS drive and reinstall.

---

### Post by Rhubarb on 2009-09-16
> **Cheesejaguar said:**
> I'm guessing there are a lot of files to be changed? I guess I'll just try to copy everything off the OS drive and reinstall.

After doing a rather basic count of files / items in my root directory on my Ubuntu laptop here, my count comes to 299,108 items!

I'm sure a large majority could be fixed easily enough as most of them would have the same permissions - a recursive chmod should be able to fix them up.  There are a few directories containing binaries, so you'd have to chmod +x these (eg /usr/bin).
If you're running a web server you may have to chown www-data all the files / directories in /var/www

The safest bet to me would be to still perform a backup and re-install.
Unless of course anyone else here would have any better suggestions.

---

### Post by eldragon on 2009-09-16
reinstall...
you will most likely leave something behind trying to fix this and it will pose as a security threat.

---

### Post by sedawk on 2009-09-16
Hello!

There might be alternatives to a full reinstall!
Giving 777 normally doesn't harm functionality, "only"
local security.

* ssh is picky about permissions because you gave public
  read access to your private key files.
  (If it is a multi-user system and you do not trust other
   users, think about recreating ssh keys ...)
  Changing your (all) private ssh files back to 600 should do
  the trick and ssh works again:

* You should change back permissions of /etc/shadow 
  to default 0640.

```

sudo chmod 755 /etc
sudo chmod 755 /etc/ssh
sudo chmod 600 /etc/ssh/ssh_host_dsa_key
sudo chmod 600 /etc/ssh/ssh_host_rsa_key
sudo chmod 640 /etc/shadow

```

* I'm not sure this is possible with Debian/Ubuntu, but
  the "package database" might contain the right permissions
  for each and every file. So there might be some kind of
  easy way to repair the permissions (with rpm packages you can
  at least do a verify to find wrong permissions or changed
  files).

* If you have a second system you can generate a list
  of files and directories with the correct permissions
  on that system and use that list as input for some
  script that repairs your system.
  (I once had to do such a recovery using the tar output of
   a previous backup that contained all the needed data.)

  Here is a hack to generate a repair script for directory
  permissions on a second Ubuntu:
```

find / -depth -type d -print |\
  while read DIR;do
    echo "# chmod "$(stat "$DIR" |\
    grep Access: | grep -o "(..../"|grep -o "[0-9]*") \"$DIR\"
  done

```
If I haven't included any typo copying that string from the
next monitor, the first lines of output will be:
```

# chmod 0755 "./opt"
# chmod 0755 "./mnt"
# chmod 0755 "./root/.gconfd"
...

```
Actually most directories should have permissions 755, so
it might be much easier to change all directories back to
755 as a start and then to check which directories used
something different.

---

### Post by Cheesejaguar on 2009-09-16
Thank you so much! I'll grab a graphics card from my junk pile and plop in a LiveCD. Thankfully since everything is 777 I *should* be able to modify it, right?

---

### Post by 5hawnk3lly on 2010-10-20
this sucks.

I was almost finished customizing a new install. Then I had some issues with permissions in Midori. I wanted to update all the file and folder permissions beginning with a "." in my home folder so i did:

```
root@mckenna:/home/skelly# chown -R skelly:users .*
```but I apparently forgot that ".*" includes "..", which recursively changed ownership (i also ran "chmod -R 0771 .*" ) and permissions for the whole system.

DUH.

Now I have nothing better to do while i reinstall than share my dim-wittedness with others.  maybe some other people can learn from my stupidity.

I am guessing this wouldn't have happened if I ran?

```
chown -R skelly:users /home/skelly/.*
```Too scared to try now...

---

### Post by wilsonr0 on 2010-12-02
I have also put my brain to one side whilst executing a chmod -R 777 .*. So easy to do and so hard to take back!

Whilst I can't offer any helpful advice perhaps you can take some consolation from not being the first or the last to make this mistake.

Rob

---

### Post by Vaphell on 2010-12-02
when running potentially destructive commands, check first what's included
```
echo .*
```
this one includes . and .. (dot followed by 0+ of whatever)

```
echo .[^.]*
```
and this one does not (dot followed by not-dot and 0+ of whatever)

---

### Post by Habitual on 2010-12-02
[The 7 Deadly Linux Commands]("http://www.junauza.com/2008/11/7-deadly-linux-commands.html") <-- Click me.

---

### Post by czr114 on 2010-12-02
Reinstall.

The system's security is now compromised. Any attempt to restore it will take far more time than a backup, reinstall, restore cycle. The fresh installation will be right, whereas a convoluted attempt to reset permissions runs the risk of missing something critical.

---

