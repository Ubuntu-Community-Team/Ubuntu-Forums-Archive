---
title: "Chmod for d---------"
date: 2010-05-25
forum: General Help
---

### Post by komitaltrade on 2010-05-25
What is the numerical value for d---------

---

### Post by CharlesA on 2010-05-25
There isn't one. That stands for "directory"

You'd need both read and execute permission to access a directory.

Read = 4
Write = 2
Execute = 1

---

### Post by Nythain on 2010-05-25
chmod u+X

---

### Post by jerome1232 on 2010-05-25
```
chmod a-rwx
```

 I don't know if there is a numeric value for that.

---

### Post by CharlesA on 2010-05-25
If they want rwx permissions they can use "7"

---

### Post by Morbius1 on 2010-05-25
Mind if I ask a stupid question. Why on earth would you want to give a directory an octal value of 000? You will render a directory inaccessible even to root.

[COLOR=Blue]EDIT: I guess that's not true since I just created a new file as root in a user directory that that has a mode of 000.[/COLOR]

I have to remember to think first then post - not the other way around:wink:

---

### Post by komitaltrade on 2010-05-25
Well it simple cant be.

I cant boot Lucid because boot is broken by Getpwuid_r. 

Here is list of permission s and you can see how from all my desktop users, just wick have drws--S--- and others are with d---------

So, I just want to revert him back like others.  [U]

root@ubuntu:/mnt/home# ls -l
total 32
drwxr-xr-x 29 1005 1005 4096 2010-05-19 22:44 games
d--------- 83 1002 1002 4096 2010-05-24 20:38 marc
d--------- 88 1001 1001 4096 2010-05-25 18:01 manager
d---------  3 root root 4096 2010-05-18 19:34 remastersys
d--------- 24 1006 1006 4096 2010-05-19 23:22 ubuntulucid
drwxr-xr-x 35 1000 1000 4096 2010-05-24 20:45 virtual
drws--S--- 71 1004 1004 4096 2010-05-25 00:17 wick
d--------- 46 1003 1003 4096 2010-05-25 17:41 windy
[/U]

---

### Post by geirha on 2010-05-25
```
sudo chmod -R u+rwX /mnt/home
```

That should make the homedirs and files inside accessible to the respective users at least.

---

### Post by komitaltrade on 2010-05-25
Geirha it worked. Now just how to remove this big S in wick (drws--S---)?

---

### Post by lykwydchykyn on 2010-05-25
> **komitaltrade said:**
> Geirha it worked. Now just how to remove this big S in wick (drws--S---)?
```

chmod -s wick

```
I think

---

### Post by komitaltrade on 2010-05-25
Its worked also, but now I at least know how permissions dont count anything with Getpwuid_r.

I still cant boot Lucid.

---

### Post by komitaltrade on 2010-05-25
wht is the default chmod for /

---

### Post by geirha on 2010-05-25
My guess is that it's not only the homedirs that have gotten odd permissions set.
```
sudo ls -l /mnt
```

What error message do you get when you try to boot now?

---

### Post by komitaltrade on 2010-05-25
Boot message is same and ls is like follow

root@ubuntu:/mnt# sudo ls -l /mnt
total 148
drwxr-xr-x   2 root root  4096 2010-05-22 07:02 bin
drwxr-xr-x   3 root root  4096 2010-05-18 22:56 boot
drwxr-xr-x   2 root root  4096 2010-05-16 01:40 cdrom
drwxr-xr-x   4 root root  4096 2010-05-16 01:41 dev
drwxr-xr-x 193 root root 12288 2010-05-25 00:00 etc
drwx------  10 root root  4096 2010-05-19 01:51 home
lrwxrwxrwx   1 root root    33 2010-05-16 02:13 initrd.img -> boot/initrd.img-2.6.32-22-generic
lrwxrwxrwx   1 root root    33 2010-05-16 01:42 initrd.img.old -> boot/initrd.img-2.6.32-21-generic
d---------  24 root root 12288 2010-05-20 09:16 lib
drwx------   2 root root 16384 2010-05-16 01:36 lost+found
drwxr-xr-x   2 root root  4096 2010-05-16 18:46 man1
d---------   4 root root  4096 2010-05-24 22:10 media
drwxr-xr-x   2 root root  4096 2010-04-23 10:11 mnt
d---------  14 root root  4096 2010-05-22 22:53 opt
drwxr-xr-x   2 root root  4096 2010-04-23 10:11 proc
drwx------  29 root root  4096 2010-05-24 22:12 root
drwxr-xr-x   2 root root  4096 2010-05-20 02:35 sbin
drwxr-xr-x   2 root root  4096 2009-12-05 21:55 selinux
d---------   3 root root  4096 2010-05-16 03:42 srv
drwxr-xr-x   2 root root  4096 2010-03-30 07:17 sys
d---------  58 root root 36864 2010-05-25 00:22 tmp
drwxr-xr-x  11 root root  4096 2010-05-20 01:46 usr
d---------  16 root root  4096 2010-05-16 08:33 var
lrwxrwxrwx   1 root root    30 2010-05-16 02:13 vmlinuz -> boot/vmlinuz-2.6.32-22-generic
lrwxrwxrwx   1 root root    30 2010-05-16 01:42 vmlinuz.old -> boot/vmlinuz-2.6.32-21-generic

---

### Post by geirha on 2010-05-25
Several important system directories has got wrong permissions. No wonder it won't boot.

Fixing that is very hard and time consuming (figuring out which permissions are correct for each file and dir). My best recommendation is to back up important data and reinstall.

Someone with sudo rights must've run a chmod in the wrong directory or something.

---

### Post by komitaltrade on 2010-05-25
Yeah, its done

chmod 0000 /

---

### Post by doas777 on 2010-05-25
> **komitaltrade said:**
> Geirha it worked. Now just how to remove this big S in wick (drws--S---)?

should be 
```

chmod 0700 <path>

```the s is for SetGID, and the S is for Sticky. I use sgid to force the owner group of the file to be that of the dir for sharing purposes. sticky forces the files to take on the ownership attrib of whoever creates them. by setting the leading digit to 0 instead of 2, it should turn it off.

---

### Post by doas777 on 2010-05-25
> **komitaltrade said:**
> Yeah, its done

chmod 0000 /

ummm, really?

---

### Post by komitaltrade on 2010-05-25
Geirha do you know how to try to revert chmod 0000 /

As I already made backup, I can start with new installation if it fail.

---

### Post by doas777 on 2010-05-25
> **komitaltrade said:**
> Geirha do you know how to try to revert chmod 0000 /

As I already made backup, I can start with new installation if it fail.

sudo chmod 0740

---

### Post by komitaltrade on 2010-05-25
Doas are you sure? It is /

Geirha, of course, it should be from live CD from /mnt

---

### Post by komitaltrade on 2010-05-25
It is not sudo chmod 0740 /mnt

---

### Post by doas777 on 2010-05-25
> **komitaltrade said:**
> Doas are you sure? It is /

Geirha, of course, it should be from live CD from /mnt


well, lets confirm,
you have changed / to 0000, right? since that won't allow you to boot effectively, you will need to loosen it some. 

most of the objects in root are owned by root:root and have drwx-rx-x permissions, giving you a permission of 761. since / contains these objects it must have at least read priv, so 740 seems a reasonably minimal set. perhaps 755 or 761 will suit you better

keep in mind, this command is only on / itself, not on any of the objects in it. if you screw it up, just use sudo to fix it (as all files are 770 to root.)

---

### Post by komitaltrade on 2010-05-25
It will not work. Geirha have right, I will start again.

P.S. How I can hide filesystem from users?

---

### Post by jerome1232 on 2010-05-25
By not allowing then in the admin group.

At least that prevents them from making changes if that is what you meant.

---

### Post by komitaltrade on 2010-05-25
No, I want to disable users to see filesystem not just to access to filesystem.

---

### Post by lykwydchykyn on 2010-05-27
> **komitaltrade said:**
> No, I want to disable users to see filesystem not just to access to filesystem.

Can't be done, AFAIK.  Why would you want to do this anyway?

---

### Post by komitaltrade on 2010-05-27
I don't believe how it cant be done. Reason is simple, it is cyber cafe and I don't want neither to let to clients to know what is behind the system, not just to disable access to the system.

Example is network in nautilus (and in menu places, what is same). This is for entire system big back-door. Network must be allowed ,because it is cyber, but problem is how client can do what he want via access from Network in nautilus.

---

### Post by jerome1232 on 2010-05-27
Put them in a chroot jail, it will effectively prevent viewing of the file-system, however it can be broken out of if one knows how.

Here is Ubuntu's documentation on it, I don't know much about the actual process of locking a user's login into a chroot jail.

[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

---

### Post by komitaltrade on 2010-05-27
Jerome, thanks. it is very interested concept (I don't expect hackers in cyber cafe, so it is perfect).

As I see, problem is just how I must completely rebuild the system (in fact, for me is not clear how to put users in jail and in the same time allow them to use applications).

---

### Post by lykwydchykyn on 2010-05-27
What things do you want to allow them to do on the desktop?  It might be easier just to come up with a locked-down desktop setup rather than trying to hide things at the system level.

I could be wrong, but my understanding of a chroot is that anything they are going to run has to be rebuilt in the chroot, so it kind of defeats the purpose.

I've messed with various ways of locking down public machines for kiosks, but my kiosks have always been just browser terminals, not actual desktops.

One idea I tried that worked well was to create a liveboot image using debianLive (though you could create an ubuntu one using remastersys or similar), then having the clients boot to it via PXE.

The net result was that the clients had a completely read-only OS that existed entirely in RAM.  If anyone messed up anything, just reboot.

---

### Post by jerome1232 on 2010-05-27
I like a kiosk oriented desktop idea as well, I was just presenting the only way I know of to truly hide the system from a user. 

When you get the setup you like create an image of it, if a system does get messed up you can just restore the image and get a clean install again.

---

### Post by komitaltrade on 2010-05-27
Thinks are come to be interested.

[lykwydchykyn]("http://ubuntuforums.org/member.php?u=603141") it is not solution to lock-down desktop setup (i will do complete GNOME lock-down), because it will not stop user to search network (other PC on LAN) and he also can be curios to search file system (as it is visible).

Chroot is great solution, but not good for me, as I already developed users with different environments (something like Edubuntu approach) and it will be impossible (hard) to make it again.

I saw before (month or two) somewhere how somebody get solution how to hide it (he done it from kids) and solution is very simple (all great thinks are simple), but I cant remember what he done (it was some trick with masking the paths).

---

### Post by lykwydchykyn on 2010-05-28
Well I've never locked down GNOME before, so I don't know what's possible; KDE3 had a kiosk tool that allowed you to prevent the file manager from leaving the user's home directory, but that tool isn't around in KDE 4 as far as I know.

I came to the conclusion that it was simpler to throw desktop environments like GNOME and KDE out and just build a minimal environment that gave the user only what I wanted them to have.  But that may not work for you.

If you find that simple solution, let us know; I'd be interested to hear it.

---

### Post by BoneKracker on 2010-05-28
> **geirha said:**
> ```
sudo chmod -R u+rwX /mnt/home
```

That should make the homedirs and files inside accessible to the respective users at least.

++

But my question is, how did they get like that?

---

### Post by BoneKracker on 2010-05-28
> **lykwydchykyn said:**
> I could be wrong, but my understanding of a chroot is that anything they are going to run has to be rebuilt in the chroot, so it kind of defeats the purpose.

Well, you can bind-mount any file or directory into the chroot, and then remount it read-only.

---

### Post by komitaltrade on 2010-05-28
Yeah [lykwydchykyn]("http://ubuntuforums.org/member.php?u=603141")  it will not work for me, because I builded the system where client can  working in his usual environment (he can choose win, mac, ubuntu, etc.),  what mean how nautilus (in explorer sense) simply must to exist for  browsing (it is not the kiosk).

So, my philosophy is originated from main problem of every cyber cafe -

RAISING % of PC USAGE

It is possible just if you try to give to the people closer as possible  commodity. It mean, for Mac users Mac like environment and application,  for windows user ...., but it also mean working in his own language  (important for touristic environments - places, hotels, etc.), it also  mean Edubuntu and Christian/Islamic approach, but it also mean separate  sessions for:

- gamers
- international calls (call shops)
- multimedia session (Internet TV, etc.) ...

Basically, one PC for many purposes and profiles.

Ubuntu is ideal for that (I builded it already), just to solve some  small issues (like this one).

Peoples who want to play games dont want to see Bible or Gimp etc and viceversa (bunch of the software bother). Solution is for every profile and purpose most natural environment (e.g. included language).

For cyber owner is same if somebody come to play game or make call or watch basketball (movie, etc.) or for classic cyber (also special tasks like CAD, Bible study, Library research, etc.). 

Goal is raising the % of PC usage.

---

### Post by lykwydchykyn on 2010-05-28
Definitely an interesting approach; locking that down isn't going to be easy.

I wish you success with it!

---

### Post by lucianindianapolis on 2010-05-29
One of my friends made a script for us. It's function is to display the valid octals for the chmod command. He posted it on his blog @ [http://evilplans.tk](http://evilplans.tk)

I believe the post is something like "command to help with chmodding". Anyhow, he created a python script that works like this:

type octal in terminal

you get this:

 
Octal Bin CHMOD
----- --- -----
  0   000  --- 
  1   001  --x 
  2   010  -w- 
  3   011  -wx 
  4   100  r-- 
  5   101  r-x 
  6   110  rw- 
  7   111  rwx 
 
Legend: r = read, w = write, x = execute
 

if you use 'octal -g' it creates a GUI that contains the table. i asked for this because I was chmodding a lot of stuff in my home directory and did not want to keep retyping 'octal' when it scrolled off screen.

---

### Post by BoneKracker on 2010-05-29
You'll be better off just to understand it, then there's nothing to memorize and no need for a script.  Also, that script doesn't tell you everything you need to know.  It seems confusing, but once you study it a bit, it all makes sense.

The permissions are four octal numbers (four "bytes"):
Special User Group Others

Each of those octal numbers is really an octal conversion of three binary switches (three "bits").

**In the first three cases** (all cases but "Special", these are "on" (1) or "off" (0) for "read", "write" and "execute" permission.  When they are layed out in sequence, as "rwx", the binary->octal conversion looks like this:

r-x -> 101 (binary) -> 5 octal

For example, rwx r-x --- would be 750.  That should take about a second in your head.

If it's the binary-to-octal conversion that's throwing you, just think like this:```
rwx rwx rwx
421 421 421
 7   7   7
```

With that picture in your head, it's easy:```
rwx r-x ---
421 401 000 
 7   5   0
``````
rw- rw- r--
420 420 400 
 6   6   4
```
```
rw- r-- ---
420 400 000 
 6   4   0
```

A few minutes of digesting that will save you many, many minutes of looking it up over time.

**Then there is the fourth byte ("Special").**  Instead of referring to "on" and "off" for "read", "write", and "execute", its bits refer to "on" and "off" for "SUID", "GUID", and "Sticky".

_SUID bit_: ("Set User Identifier"):

- On a file: when this file is executed, the process will have the rights of it's owner, no matter who executed the file

- On a directory: N/A

_SGID bit_: ("Set Group Identifier")

- On a file: when this file is executed, the process will have the rights of it's group, no matter who executed the file

- On a directory: all files in this directory automatically inherit the GID of the directory

_Sticky bit_:

- On a file (obsolete: not used any more)

- On a directory: a file in this dir can only be _deleted_ by its owner (regardless of group or other write permissions)

So, it's just like another "rwx", but it's "SUID-SGID-Sticky".```
SUID SGID Sticky
  4    2    1

```
So if you set up a shared directory say, to be used between your users, and you want all users to be able to read and write to any file there, but you don't want people deleting files other people have put in there, what would you do?  You'd want SGID on the directory and Sticky on the directory:```
SUID SGID Sticky
  0    2     1
       3

```

So, if your other permissions on the directory were:```
rwx rwx ---
 7   7   0
```
Then the overall permissions (the directory's "mode"), would be "3770".

That all makes pretty good sense.  You just have to remember "rwx -> 421" and "SUID, SGID, Sticky". :)

But there's one complication.  When SUID, SGID, and Sticky were added, to avoid making the textual representation of permissions (rwx rwx rwx) any longer (like say "sss rwx rwx rwx"), it was decided to overlay that symbol on the execute symbol.

Owner (in x place):
S -> SUID bit is set
s -> SUID and execute are both set

Group (in x place)
S -> SGID bit is set
s -> SGID and execute are both set

Others:
T -> Sticky bit is set
t -> Sticky and execute are both set

So, the textual representation of our 3770 mode from the shared directory example above would be:
```
rwx rws --T
```

The only other weird thing is the use of the capital X with the chmod command, but that's easily understood from the chmod man page.

---

### Post by doas777 on 2010-06-01
> **BoneKracker said:**
> <snip/>

thank you, that was the most concise description of the special permissions I have seen.

---

### Post by BoneKracker on 2010-06-01
> **doas777 said:**
> thank you, that was the most concise description of the special permissions I have seen.
Thanks for saying so.

I wouldn't have bothered, but it's one of the things that were persistently confusing to me, and I found most explanations to be lacking in some way.

Hopefully, it's actually correct. :P

---

