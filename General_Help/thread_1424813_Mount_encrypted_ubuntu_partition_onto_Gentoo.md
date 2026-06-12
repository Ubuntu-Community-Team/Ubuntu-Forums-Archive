---
title: "Mount encrypted ubuntu partition onto Gentoo"
date: 2010-03-08
forum: General Help
---

### Post by deanhopkins on 2010-03-08
Hi, ive recently switched to Gentoo as my primary OS - the only problem im having so far is getting my ubuntu partition to mount, aparantly it is encrypted, although i cannot remember ever doing this.

It is an ext4 filesystem. When I do

su
mount /dev/sdb1 /media/Ubuntu

It mounts, but when I cd to /media/Ubuntu/home/dean all I see is a blank README.txt and Access-Your-Prive-Data.desktop files.

Is it possible for me to mount my ubuntu partition to be read / written to in gentoo? If not, how do I go about removing the encryption? (I still have access to the ubuntu install)

Thanks.

---

### Post by deanhopkins on 2010-03-09
Bump :(

---

### Post by God Of Atheism on 2012-01-28
Did you manage to solve this? I'm running into the nearly the same problem. Although it's not my home partition that is encrypted, but my home directory.

---

### Post by God Of Atheism on 2012-01-29
I did manage to solve it by removing the encryption, following [these instructions]("http://www.satansgarden.org/2010/03/05/removing-encryption-from-home-directories-in-ubuntu-9-10/"). This is of course a workaround instead of mounting the encrypted partition in Gentoo.

I did have a problem with moving the files though. For some reason mv copied instead of moved when I tried to move the files from ~/Private to ~. As a result I ran out of disk space. When I moved the files to a different partition they did actually move. If you need to move to the same partition, then try to move less than your free space on that partition in one go and my guess is that it should be okay.

---

### Post by bodhi.zazen on 2012-01-30
You are both looking at ecrypfs

To enable it in gentoo see

[http://en.gentoo-wiki.com/wiki/Encrypt_home_directory_with_ecryptfs](http://en.gentoo-wiki.com/wiki/Encrypt_home_directory_with_ecryptfs)

[http://en.gentoo-wiki.com/wiki/Ecryptfs](http://en.gentoo-wiki.com/wiki/Ecryptfs)

You should be able to mount the ubuntu home in a chroot

[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live_CD_method_of_opening_a_encrypted_home_directory)

And if that is the "only problem" you had with gentoo, you are doing well.

---

### Post by Khayyam on 2012-01-31
> **bodhi.zazen said:**
> [..] And if that is the "only problem" you had with gentoo, you are doing well.
bodhi ..

I don't think there is really any grounds on which to say that, it comes across as your having been slighted for someone switching (and that is what the "only problem" in the the post refers to).

Gentoo has alot going for it, and I say that as someone who has some experience in that regard and can attest to all kinds of "problems". I was at one point a Gentoo developer, but left as I was unhappy with how the project was managed. Still, as a distribution it 'mostly' works as advertised. I can point to various installs I've done (some as far back as 2001) that are to this day ['rolling releases']("http://en.wikipedia.org/wiki/Rolling_release").

That said, I can see a place for both Gentoo and Ubuntu, I more often refer people to Ubuntu when asked for a recommendation (which, in fact, was the reason I ended up creating an account here) but I'd most likely choose Gentoo myself for most tasks. Partly its familiarity, partly its the kind of tasks I'm empolyed to do, partly its a preference for Gentoo's way of doing things .. but I'd never say that one somehow tops the other, or that given some percieved "problem" gentoo was the only viable choice (and yes, reading some of the posts here I could point to "problems" that could be labled 'symptomatic' of Ubuntu's design). Mostly its besides the point, I'm not going to have to use someone elses install, and I don't have that strong a sense of brand loyalty to insist they agree with my evaluation and/or preferences. If someone says I'm migrating from Gentoo to Ubuntu, or visa-versa, I'm more inclined to say "good for you".

Anyhow, I'm not sure what your intentions were, perhaps I'm misreading the whole thing. 

best ..

---

### Post by bodhi.zazen on 2012-01-31
> **Khayyam said:**
> Anyhow, I'm not sure what your intentions were, perhaps I'm misreading the whole thing. 

best ..

I think you are misreading the whole thing. 

I am a current gentoo user. Gentoo is a nice distribution, but, as with all distros, including Ubuntu, there are problems from time to time.

With that said, I would not characterize gentoo as "easy to use" or problem free.

Just compare the install guides

Gentoo [http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=1](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=1)

12 (well mostly 11) chapters, mostly manually configuration.

Ubuntu - [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

10 steps, mostly automated.

If you can not appreciate the difference, then there is not much to the conversation.

---

### Post by Khayyam on 2012-02-01
> **bodhi.zazen said:**
> I think you are misreading the whole thing.

I am a current gentoo user. Gentoo is a nice distribution, but, as with all distros, including Ubuntu, there are problems from time to time.
OK, but this is then a question of 'relative merits'. The statement "if that was the "only problem" you had with gentoo, you are doing well" suggests that Gentoo has "problems" above and beyond those we might expect "from time to time".

> **bodhi.zazen said:**
> With that said, I would not characterize gentoo as "easy to use" or problem free.
Agreed, but no more or less "problem free", which is not what your statement suggests.

> **bodhi.zazen said:**
> Just compare the install guides [...]
These are relative merits. The fact that the install methods differ and that one has comparatively less steps does not mean that one or other will be less prone to "problems". An installer is less intelligent than a human and can fail if certain conditions aren't met, a human might catch a potential problem that an installer may overlook or fail to forsee, but the installer has the advantage of "ease of use", time requirements, etc, which means there is less required from the user to opperate it. So, each has its merits, but they are offset by other factors.
  
> **bodhi.zazen said:**
> If you can not appreciate the difference, then there is not much to the conversation.
Huh? What am I failing to "appreciate"?

---

### Post by bodhi.zazen on 2012-02-01
> **Khayyam said:**
> Huh? What am I failing to "appreciate"?

Most people do not find Gentoo to be "user friendly", and most people are intimidated by a 12 page install guide.

Most people do not want to manually configure their wireless card, manually run fdisk, do a command line install, in a chroot, without graphical tools.

If you like that sort of thing, there is much to learn, but most people do not want to perform such low level tasks to the nth degree. Most people want to spend their time using their computers to perform what the see as productive tasks, and not setting compile flags.

I think you are failing to appreciate why Ubuntu is more popular then gentoo.

---

### Post by paradigm2 on 2012-02-01
I know the Gentoo vs Ubuntu discussion is not the original topic but I thought I'd put my two cents in.  I've been a Gentoo and Arch user for the past three years.  I've also dabbled with Slackware briefly as well.  For one of the reasons bodhi.zazen stated I'm considering going back to *buntu.  It's not that I don't know how to maintain my system or set it up under Gentoo or Arch, it's more precisely that I want to spend more of my time being productive (or watching movies. ;)). To each their own.  Each has their strengths and weaknesses.

---

### Post by Khayyam on 2012-02-02
> **bodhi.zazen said:**
> Most people do not find Gentoo to be "user friendly", and most people are intimidated by a 12 page install guide.
Which is an entirely seperate question, what "most people find" is, as I said, a matter of "relative merits". As I have been at lenghts to make clear, this is unrealated to your statement. You didn't say "most people find installing Gentoo more difficult, and Ubuntu less so" or "the install guide is less intimidating" but **"if that was the "only problem" you had with gentoo, you are doing well"**. To make it absolutely clear, I am not making a case for one or other distribution, if you read what I have written carefully, you will see that I am **entirely** in agreement with you as to the question of "ease of use" and what-have-you, but, again, that is an entirely seperate question.

> **bodhi.zazen said:**
> Most people do not want to manually configure their wireless card, manually run fdisk, do a command line install, in a chroot, without graphical tools.
.. and "most people" are free to choose not to do so .. again, a seperate question to the the above stated "only problem".

> **bodhi.zazen said:**
> If you like that sort of thing, there is much to learn, but most people do not want to perform such low level tasks to the nth degree. Most people want to spend their time using their computers to perform what the see as productive tasks, and not setting compile flags.
.. and "people" are free to choose how they "want to spend their time" .. again, a seperate question to the the above stated "only problem".

> **bodhi.zazen said:**
> I think you are failing to appreciate why Ubuntu is more popular then gentoo.
I see, so your running a popularity contest? Given that I wasn't promoting any candidate, and "appreciate" the relative merits of both, I'm obviously failing to appreciate the value of popularity, or why you feel it necessary to suggest that my failings are as partisan as yours, rather than answer to the objection as I posed it.

I'm getting the impression that however clear I try to be this discussion has already been made one where partisanship is the central issue. Of course, Gentoo is the better, for all things, under all circumstances, for all purposes, just compare the install guides .. there, I said it, we can now speak past each other with happy abandon!

---

