---
title: "How I (accidentally) logged in as ROOT !?!"
date: 2010-08-26
forum: General Help
---

### Post by Flash858 on 2010-08-26
OK, this threw me, as I did not think logging in as root was possible in Ubuntu. Perhaps someone can shed some light...

I am a professional photographer, and occasionally, and usually at gunpoint, I am forced to be a web designer, and/or a graphics designer for a client. I am perfectly skilled at this, but I don't really enjoy it, nor do I do either very efficiently (note the reference to the aforementioned loaded gun...).

I have a job I am bidding on, and it involves shooting, writing the copy for, designing, and printing a tri-fold brochure for a venue. As I am trying to free myself of the Windows environment entirely, I was looking for some new Linux graphics tools. 

Not wanting to just go through the repositories searching, I instead installed ArtistX on a small partition. It is an Ubuntu derivative that seems to have virtually every graphics program I have ever heard of, and MANY I have not heard of, for Linux. I intend to find some new tools, then just install the packages on my production Ubuntu partition.

For some reason, it would not install the Nvidia driver even though it is based on 9.04, so I went to Nvidia and downloaded the proprietary driver. As it is a .run file, it must be sh'ed from a terminal, so I logged in to failsafe terminal, stopped the X-server (sudo /etc/init.d/gdm stop), logged in, and installed the driver. When it was complete, I simply ran "sudo startx", and it popped up nicely. However, I was logged in as ROOT!

Is this normal? Does it make sense? Will Ninja Clowns come after me? Do I need to repent?

I never knew this was possible, so someone please enlighten me. I am afraid to make any changes, as I do not want to hose permissions when I log in normally, but it sort of weirded me out.

Comments will be appreciated...:o

---

### Post by snowpine on 2010-08-26
Hi there, ArtistX is not, strictly speaking, Ubuntu, so you might get better advice on the ArtistX forums. :)

That being said, it is possible to log in to failsafe/recovery mode in Ubuntu without a password. This is a frequently-asked security question here on these forums. The short answer is "physical access is root access" and you should encrypt your hard drive if you plan to give untrusted strangers physical access to your computer.

---

### Post by sisco311 on 2010-08-26
> **Flash858 said:**
> 
Is this normal? Does it make sense? 


Yes, sudo executes a command as another user, by default root and startx starts an X session.

> **Flash858 said:**
> 
Will Ninja Clowns come after me?


Yes. =)

---

### Post by Flash858 on 2010-08-26
Snowpine - I believe you missed the upshot of my question entirely.

I am not concerned about security.

Not one iota.

I simply wanted to know if this circumvention is normal, or if something went wonky.

---

### Post by snowpine on 2010-08-26
> **Flash858 said:**
> Snowpine - I believe you missed the upshot of my question entirely.

I am not concerned about security.

Not one iota.

I simply wanted to know if this circumvention is normal, or if something went wonky.

It is a normal feature of the operating system; it allows you to recover your system in case of a hard disk error, you forget your password, etc.

---

### Post by Flash858 on 2010-08-26
Sisco - By killing the xserver as root, and restarting X, I effectively logged in as root, correct?

If this is possible, why not just have the ability to log in as root? I frankly think that this should be possible, and now that I know it can be done, I think I will write a login script to do it for me (this is what I was driving at). 

I don't care about security. I mean, my machine is in my own home, I have a server with tons of security for my internet connection, and my wi-fi has mac filtering and does not broadcast. I get quite annoyed having to type in passwords on my own damn system, and not having access to my own damn partitions (which is why I loathe XFCE).

Someone needs to create "Rootbuntu"... ;)

---

### Post by Flash858 on 2010-08-26
Oh, and the reason I am so fascinated with this is that I have been running Ubuntu since 7.10 (4 years, I guess?), and I never knew this. As I mentioned above, I want root access at all times, as I do not like being hampered, and no one uses my computers but me. 

I am quite excited... :)

Shebang! Off to write that shell script...  ;)

---

### Post by snowpine on 2010-08-26
I do not recommend logging in as root or using the "failsafe terminal" for everyday computing. You are free to do as you like on your computer, but please consider [embracing 'sudo']("https://wiki.ubuntu.com/RootSudo"). :)

---

### Post by sisco311 on 2010-08-26
> **snowpine said:**
> I do not recommend logging in as root or using the "failsafe terminal" for everyday computing. You are free to do as you like on your computer, but please consider [embracing 'sudo']("https://wiki.ubuntu.com/RootSudo"). :)

+1

@OP
sudo and policykit are very flexible and customizable applications. You can disable the password prompt for certain (or all) applications if you wish.

---

### Post by coffeecat on 2010-08-26
Oops, posted in error.

---

### Post by TwoEars on 2010-08-26
> **dagdeniz said:**
> Ubuntu is not an OS, it's a Linux distribution. Like every other Linux distribution, you have a root user, although it is not activated by default in Ubuntu. You only need to enter a password for it to activate. To do this:
```

<snip>
```
and enter a password. To login as root (I wouldn't recommend, there is the gksu thing instead), you need to change gdm preferences. 

and...
Using sudo is not necessarily safer than having a root user (nor the opposite is necessarily true). Much has been talked about it so far, you can google it.

+1

I suggest doing this even if you aren't planning to use root. It'll add that extra level of safety, if this ArtistX allows root logins, it's better to have a root login which requires a password.

---

### Post by endotherm on 2010-08-26
> **Flash858 said:**
> Snowpine - I believe you missed the upshot of my question entirely.

I am not concerned about security.

Not one iota.

I simply wanted to know if this circumvention is normal, or if something went wonky.
well, starting x with sudo isn't normal so I kinda understand what is happening. just out of curisoity, if you open a terminal and run 'pwd' does it print the path to your users home folder or to /root? my guess is that it is pointing to your home, meaning you are a normal user impersonating root for this shell, which is what I would generally expect.

---

### Post by endotherm on 2010-08-26
> **TwoEars said:**
> +1

I suggest doing this even if you aren't planning to use root. It'll add that extra level of safety, if this ArtistX allows root logins, it's better to have a root login which requires a password.
i don;'t really agree, but since this isn't the thread to discuss it in, I will simply say that in many many scenarios, it is better to not have a working root account.

---

### Post by cariboo on 2010-08-26
We don't care what you do with your own computer, it just that running as root all the time is dangerous, not only to you, but others too.

To the op if you do want to run as root all the time, at least read the [RootSudo Howto]("https://help.ubuntu.com/community/RootSudo"), so you understand what you are getting into.

---

### Post by Flash858 on 2010-09-19
I totally understamd all of the above comments, but this really was not about root being good or bad, but rather how an odd sequence of events got me logged into an Ubuntu variant as the root user, as it was totally unexpected behavior, and I learned something from it.

That said, I use Puppy linux as well, and it uses a single, root user by design. There are no options to add users nor groups. I use it to fix things in Ubuntu constantly, as it is just easier than typing long commands preceeded by "sudo" or using a Nautilus script, which does not always work the way I want it to, as it can change file permissions to root only if you copy/move files (etc).

While I do use the terminal, with the exception of a few things like converting video formats, I am almost always using sudo in the terminal anyway, so if I hose my machine with a terminal command, using sudo only means that I have to enter a password to do so. Moreover, I have a root terminal shortcut made, but I usually forget to use it. If I do something stupid, I am going to do it, and a password will not protect me one bit.

On a standalone computer, I just don't see the point of NOT having root at all times. At least not for my purposes...

---

### Post by Serpher on 2010-09-19
Having a root account isn't just to stop normal users from getting full power to do what they want to your computer, but your applications. If you log in to GNOME as root, and turn on Firefox, Firefox now has the power to do what they want to your computer. If you go on a website with javascript that downloads a bunch of viruses to your computer, it will work, and those viruses will be owned by root and therefore have the powers of root and possibly destroy your whole system locking you out of root or whatever.

Also what you're describing is similar to the commmand 'sudo passwd'. If you type that in, it changes the root password rather than just the command 'passwd' changing the password of the account you're currently on.

Finally if you don't want to keep typing in sudo before commands, use the i switch: 'sudo -i'. This will log you in as root IN THE TERMINAL and not the GUI which is the way it should be. Just don't start any applications like firefox from that root terminal.

---

### Post by Chris1274 on 2010-09-19
> **cariboo907 said:**
> We don't care what you do with your own computer, it just that running as root all the time is dangerous, not only to you, but others too.
 
How is it dangerous to others?

---

### Post by Old *ix Geek on 2010-09-19
> **Flash858 said:**
> I have been running Ubuntu since 7.10 (4 years, I guess?), and I never knew this. As I mentioned above, I want root access at all times, as I do not like being hampered, and no one uses my computers but me.It is, and always has been, very easily possible to set (K)Ubuntu up to allow root to login. I do it every time I do a new install. The thing is, if I tell you how to do it, I'll get in trouble and the info will be deleted: It's not allowed on these boards.

With that said, I understand that you don't like being hampered and you want root access all the time. Would you like a little advice from someone who started using UNIX in 1986? Back then, and with all power over the company's computer system as its programmer and sysadmin, I frequently did everything as root. HOWEVER, I was hyper-aware of the fact that with one errant keystroke, one misplaced command [thinking I'm in one directory when I'm really in another], I could cripple the system. But I also knew I could FIX it--and that I ALWAYS had current backups.  If you inadvertently screw something up and render your computer unusable, or irrevocably delete a directory accidentally--that contained critical files, etc., can you fix it? If the answer is truly yes, go for it. Otherwise, just make **sudo** your friend. :)

---

### Post by Flash858 on 2010-10-16
The answer is yes. I am a digital packrat, and I format every partition on every machine about every six months. I keep ZERO data on my system locally - it is all on secondary, tertiary, removable, and cloud drives, and has been for years. I could convert to a cloud based OS right now, and not even notice. 

As a Windows user/convert, I learned the EASY way was to reinstall every 6 months. It actually takes FAR less time than trying to "maintain" a system.

Hence, my desire for root access. 

Thanks for the tips!

---

