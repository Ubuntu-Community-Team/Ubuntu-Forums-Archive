---
title: "Should I wait for the final release?"
date: 2006-05-13
forum: General Help
---

### Post by Hoffmann on 2006-05-13
Hello Guys;

I have read several posts about upgrading to Dapper. Well, I am anxious to have that new version of Ubuntu installed on my machine.
So, my questions are:

(1) Shoud I wait for the final version of Dapper? 
(2) Is it a good idea to install the beta-2 version of Dapper? 
(3) If I Install the beta version, how is the procedure to upgrate from beta to the final version?
(4) What are the pros and cons of installing the beta version?

Thanks!
Hoffmann

---

### Post by aysiu on 2006-05-13
[QUOTE=Hoffmann]
(1) Shoud I wait for the final version of Dapper?[/quote] Do you use Ubuntu for work or for fun? Will you be really upset if for a day or two an application isn't working or constantly crashes on you? > (2) Is it a good idea to install the beta-2 version of Dapper? If you want to file bug reports and you don't mind an application or two being unusable from time to time. > (3) If I Install the beta version, how is the procedure to upgrate from beta to the final version? Just keep clicking on the update notifications as they appear. > (4) What are the pros and cons of installing the beta version? Pros: feel as if you're on to something new, discover new features, get more up-to-date versions of software. Cons: lose productivity.

---

### Post by barbarian on 2006-05-13
Hello.
Do you desperately need to install Dapper today? If not, better to wait 2 weeks IMHO..

---

### Post by barbarian on 2006-05-13
Hello.
Do you desperately need to install Dapper today? If not, better to wait 2 weeks IMHO..

---

### Post by barbarian on 2006-05-13
Hello.
Do you desperately need to install Dapper today? If not, better to wait 2 weeks IMHO..

---

### Post by barbarian on 2006-05-13
Hello.
Do you desperately need to install Dapper today? If not, better to wait 2 weeks IMHO..

---

### Post by xXx 0wn3d xXx on 2006-05-13
[QUOTE=Hoffmann]Hello Guys;

I have read several posts about upgrading to Dapper. Well, I am anxious to have that new version of Ubuntu installed on my machine.
So, my question are:

(1) Shoud I wait for the final version of Dapper? 

That depends, I have found Dapper to be very stable. I am running Beta 2 and everything is fine. Nothing broke and I have never had a crash.

(2) Is it a good idea to install the beta-2 version of Dapper? 

Refer to (1)

(3) If I Install the beta version, how is the procedure to upgrate from beta to the final version?

You would just run "sudo apt-get update" and then "sudo apt-get upgrade" just like upgrading a program like wine in breezy. 

(4) What are the pros and cons of installing the beta version?

It is still under devolopment so it might not be 100 % stable but Dapper works very well.

Thanks!
Hoffmann[/QUOTE]

I would recommend that you backup your home partition and do a clean install. A dist-upgrade is not 100 % effective and it may break your system/leave it very slow.

---

### Post by Hoffmann on 2006-05-13
Hello Guys:

Many thanks for the nice explanations!
Well, since I not only use Ubuntu for fun, but also for work, I will wait for the final version. We are almost there, aren't we?

---

### Post by aysiu on 2006-05-13
A dist-upgrade will never affect your /home folder (settings and documents), but it may kill your x server, so you'd have to know how to retrieve your /home folder without graphics or restore your graphics.

---

### Post by barbarian on 2006-05-13
> We are almost there, aren't we?

yee, two weeks worth to wait for really brilliant distro8) 

p.s. oops triple post, sorry:eek:

---

### Post by Hoffmann on 2006-05-13
[QUOTE=aysiu]A dist-upgrade will never affect your /home folder (settings and documents), but it may kill your x server, so you'd have to know how to retrieve your /home folder without graphics or restore your graphics.[/QUOTE]

aysiu:

In my case my /home "stuff" is not a partition; it is just a /home directory. Is that a problem?
One more concern I have is my /usr/local directory. I have installed/compilled several important programs I use for work. Some of those programs are not released together with Ubuntu.
What should I do in this scenario? 

One more question: do you think I should have problems regarding the x sever, after I upgrade to the final Dapper? How could I overcome eventual problems with x server?

---

### Post by aysiu on 2006-05-13
> **Hoffmann]aysiu:

In my case my /home "stuff" is not a partition said:**
>  No, it's not a problem--either way, a dist-upgrade won't affect your files. > One more concern I have is my /usr/local directory. I have installed/compilled several important programs I use for work. Some of those programs are not released together with Ubuntu.
What should I do in this scenario? Create a separate /usr partition, and while you're at it create a separate /home partition. That way, in case a dist-upgrade messes up Ubuntu, you can do a clean reinstall and do subsequent reinstalls on subsequent new releases.

[quote]
One more question: do you think I should have problems regarding the x sever, after I upgrade to the final Dapper? No, but it did happen a lot in the Hoary to Breezy upgrades, as did weird locale errors. > How could I overcome eventual problems with x server? I guess it depends on the problem. If you're not comfortable diagnosing that sort of thing, I would definitely wait three weeks to do the upgrade.

---

### Post by Hoffmann on 2006-05-13
[QUOTE=aysiu]Create a separate /usr partition, and while you're at it create a separate /home partition. [/QUOTE]
aysiu:

I liked your suggestion for creating the /usr and /home partitions. I have neve done that before. Could you give me some help in this regard? What is the procedure for doing that?

In my case, I have 3 partitions:
(1) FAT32 for Windows system recovery (about 10 GB)
(2) NTFS partition for Windows XP (about 60 GB)
(3) ext3 for Ubuntu (about 165 GB)
(4) linux-swap (about 3GB)

Can I use GParted for creating those partitions? How?

Thanks

---

### Post by aysiu on 2006-05-13
I know in theory how it should be generally done, but I wouldn't feel comfortable giving you specific instructions because I've never done it with an existing installation, and I don't know if I know enough about what the complications could be.

Generally, you would create a new partition, copy over the /usr directory to it, edit your /etc/fstab to include that partition, and finally delete the /usr folder from the original directory.

Wait for someone more knowledgeable than I am to give you more specific instructions.

---

### Post by Hoffmann on 2006-05-13
[QUOTE=aysiu]I know in theory how it should be generally done, but I wouldn't feel comfortable giving you specific instructions because I've never done it with an existing installation, and I don't know if I know enough about what the complications could be.

Generally, you would create a new partition, copy over the /usr directory to it, edit your /etc/fstab to include that partition, and finally delete the /usr folder from the original directory.

Wait for someone more knowledgeable than I am to give you more specific instructions.[/QUOTE]

Many thanks, once again!

---

### Post by Hoffmann on 2006-05-13
[QUOTE=aysiu]I know in theory how it should be generally done, but I wouldn't feel comfortable giving you specific instructions because I've never done it with an existing installation, and I don't know if I know enough about what the complications could be.

Generally, you would create a new partition, copy over the /usr directory to it, edit your /etc/fstab to include that partition, and finally delete the /usr folder from the original directory.

Wait for someone more knowledgeable than I am to give you more specific instructions.[/QUOTE]
aysiu,

Wait. But, I have an external HD. So, what about I just copy both /home and /usr partitions to that HD? After that, all I would need to do is to copy those folders (home and usr) back to my (upgraded) Ubuntu partition, if necessary. What do you think?

---

### Post by aysiu on 2006-05-13
[QUOTE=Hoffmann]aysiu,

Wait. But, I have an external HD. So, what about I just copy both /home and /usr partitions to that HD? After that, all I would need to do is to copy those folders (home and usr) back to my (upgraded) Ubuntu partition, is necessary. What do you think?[/QUOTE] Ah, an external hard drive. Excellent.

Yes, but I would .tar them instead of copying the files straight as is.

Allow for the possibility that if you don't know *exactly* what you're doing, you may have to do a clean reinstall of Ubuntu, and if that's the case, it will be very easy to set up new partitions mounted a /usr, /home, and /

After that, you could just un-tar your saved /usr and /home to the new partitions.

---

