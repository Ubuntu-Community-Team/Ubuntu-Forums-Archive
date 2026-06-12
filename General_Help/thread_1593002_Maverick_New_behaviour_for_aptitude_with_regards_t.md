---
title: "Maverick: New behaviour for aptitude with regards to unused packages?"
date: 2010-10-11
forum: General Help
---

### Post by gspr on 2010-10-11
Hi.

After upgrading from Lucid to Maverick, I've found that aptitude/apt-get have seemingly begun to treat automatically installed packages differently from before.

Start with a system that has the packages gcc and gcc-4.4. Say you then install gcc-4.5 (alongside gcc-4.4). It depends on libmpc2, so this gets pulled in aswell. Then you decide to stick with GCC 4.4 only, so you uninstall gcc-4.5. If my memory isn't playing tricks, this would have caused libmpc2 to be autoremoved (automatically with aptitude, upon calling the autoremove command with apt-get) in previous versions of apt (at least the one in Lucid). Now, in Maverick, libmpc2 is kept. Why? Let's ask...

$ aptitude why libmpc2
i   libtool Depends  gcc | c-compiler
p   gcc-4.5 Provides c-compiler
p   gcc-4.5 Depends  libmpc2

I see. I had libtool from before, which depends on the gcc OR the c-compiler metapackage. gcc-4.5 provides c-compiler and depends on libmpc2. But gcc-4.5 is no longer around, and gcc-4.4 (which has been installed all along) of course also provides c-compiler.

Again, if I recall correctly, apt{itude,-get} used to reason that "libmpc2 was only depended on by gcc-4.5, which is no longer installed. Therefore, it can be autoremoved." Now it seems to think that "libmpc2 is depended on by gcc-4.5. libtool, which is installed, needs a c-compiler, which gcc-4.5 does provide -- hence we need libmpc2."

Has there been a deliberate change of behaviour, or should I file a bug?

Thanks!

---

### Post by mc4man on 2010-10-11
Don't see that here - as a test removed gcc-4.5 (and the 3 related, g++-4.5, [COLOR="Blue"]cpp-4.5[/COLOR], libstdc++6-4.5-dev
Then both will show libmpc2 for removal

The following packages will be REMOVED:
  libcloog-ppl0 libdvbpsi5 libgmpxx4ldbl libmpc2

The following packages will be REMOVED:  
  banshee libcloog-ppl0{u} libdvbpsi5{u} libgmpxx4ldbl{u} libmpc2{u}

Do you have cpp-4.5 installed?

---

### Post by gspr on 2010-10-11
> **mc4man said:**
> Do you have cpp-4.5 installed?

Nope. This is very strange. Here's what happens for me:

```

$ sudo aptitude install gcc-4.5
The following NEW packages will be installed:
  cpp-4.5{a} gcc-4.5 libmpc2{a} 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/11.8MB of archives. After unpacking 26.7MB will be used.
Do you want to continue? [Y/n/?] y
Selecting previously deselected package libmpc2.
(Reading database ... 207775 files and directories currently installed.)
Unpacking libmpc2 (from .../libmpc2_0.8.2-1build1_amd64.deb) ...
Selecting previously deselected package cpp-4.5.
Unpacking cpp-4.5 (from .../cpp-4.5_4.5.1-7ubuntu2_amd64.deb) ...
Selecting previously deselected package gcc-4.5.
Unpacking gcc-4.5 (from .../gcc-4.5_4.5.1-7ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Setting up libmpc2 (0.8.2-1build1) ...
Setting up cpp-4.5 (4.5.1-7ubuntu2) ...
Setting up gcc-4.5 (4.5.1-7ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
                                         
$ sudo aptitude remove gcc-4.5
The following packages will be REMOVED:  
  gcc-4.5 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 15.3MB will be freed.
(Reading database ... 207866 files and directories currently installed.)
Removing gcc-4.5 ...
Processing triggers for man-db ...
                                         
$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

$ aptitude why libmpc2 
id  cpp-4.5 Depends libmpc2
$ aptitude why cpp-4.5
i   libtool Depends  gcc | c-compiler          
p   gcc-4.5 Provides c-compiler                
p   gcc-4.5 Depends  cpp-4.5 (= 4.5.1-7ubuntu2)

```

Actually, now something is different! Now it says it's keeping libmpc2 to satisfy cpp-4.5. But there's still a problem: Now cpp-4.5 should have been autoremoved.

---

### Post by mc4man on 2010-10-11
> Now cpp-4.5 should have been autoremoved. 
I generally use synaptic - so for instance if I install gcc-4.5 then cpp-4.5 is dep'ed and marked as auto
Then after just removing gcc would produce - 

The following packages will be REMOVED:
  cpp-4.5 libcloog-ppl0 libdvbpsi5 libgmpxx4ldbl libmpc2

---

### Post by gspr on 2010-10-11
> **mc4man said:**
> I generally use synaptic - so for instance if I install gcc-4.5 then cpp-4.5 is dep'ed and marked as auto
Then after just removing gcc would produce - 

The following packages will be REMOVED:
  cpp-4.5 libcloog-ppl0 libdvbpsi5 libgmpxx4ldbl libmpc2


That's exactly how aptitude behaved before I upgraded. I'm wondering if it's a bug or an intentional change.

---

### Post by dino99 on 2010-10-11
they have both their own rules to deal with packages. Some users have a better feelling with one or the other, but usually its better to use only one on your system as their database is different.

---

### Post by gspr on 2010-10-11
> **dino99 said:**
> they have both their own rules to deal with packages. Some users have a better feelling with one or the other, but usually its better to use only one on your system as their database is different.

What do you mean by "they"? Aptitude and Synaptic? I don't use Synaptic at all. I'm just trying to figure out whether aptitude's behavioural change was intentional or not.

---

### Post by dino99 on 2010-10-11
> **gspr said:**
> What do you mean by "they"? Aptitude and Synaptic? I don't use Synaptic at all. I'm just trying to figure out whether aptitude's behavioural change was intentional or not.

aptitude/apt-get

---

### Post by gspr on 2010-10-11
> **dino99 said:**
> aptitude/apt-get

Ah, I see. I actually thought they shared databases. Thanks for the info :)

But still, it shouldn't affect my situation I guess.

---

### Post by dino99 on 2010-10-11
> **gspr said:**
> Ah, I see. I actually thought they shared databases. Thanks for the info :)

But still, it shouldn't affect my situation I guess.

you might digg the synaptic changelog to know exactly about the latest mod

---

### Post by mc4man on 2010-10-11
Starting fresh, none installed- 
apt-get performs as expected
The following packages will be REMOVED:
  cpp-4.5 libcloog-ppl0 libgmpxx4ldbl libmpc2 libppl-c2 libppl7

Again starting fresh using  just aptitude to install gcc and then remove gcc shows
<The following packages will be REMOVED:>  
<nothing>

Using aptitude to install, apt-get to remove, then aptitude shows

The following packages will be REMOVED:  
   cpp-4.5{u} libcloog-ppl0{u} libgmpxx4ldbl{u} libmpc2{u} 
  libppl-c2{u} libppl7{u}

---

### Post by gspr on 2010-10-11
> **mc4man said:**
> Starting fresh, none installed- 
apt-get performs as expected
The following packages will be REMOVED:
  cpp-4.5 libcloog-ppl0 libgmpxx4ldbl libmpc2 libppl-c2 libppl7

Again starting fresh using  just aptitude to install gcc and then remove gcc shows
The following packages will be REMOVED:  
<nothing>

Using aptitude to install, apt-get to remove, then aptitude shows

The following packages will be REMOVED:  
   cpp-4.5{u} libcloog-ppl0{u} libgmpxx4ldbl{u} libmpc2{u} 
  libppl-c2{u} libppl7{u}

Aha, that certainly is interesting! Something is indeed amiss with aptitude, it seems.

---

### Post by mc4man on 2010-10-11
edit
of no value

---

### Post by gspr on 2010-10-11
> **mc4man said:**
> I think maybe not, though this can get a bit confusing....

Try a fresh start, use just aptitude but after the remove close and open a new terminal, it appears then it will find the auto installed.
Normally one wouldn't install and remove from the same terminal.
(or this is inconsistent behaviour

Hmm, no not here I'm afraid.

---

### Post by mc4man on 2010-10-11
> Hmm, no not here I'm afraid.

Your right, was using the arrow key to repeat - actually used apt-get to remove

So it appears that if aptitude installs and removes that then the auto installed are 'lost'

---

### Post by gspr on 2010-10-11
> **mc4man said:**
> Your right, was using the arrow key to repeat - actually used apt-get to remove

So it appears that if aptitude installs and removes that then the auto installed are 'lost'

Yep, we agree. And this certainly did not happen in Lucid and earlier. I'm leaning towards filing a bug. I'll throw in a link when that's done.

---

### Post by gspr on 2010-10-11
> **gspr said:**
> Yep, we agree. And this certainly did not happen in Lucid and earlier. I'm leaning towards filing a bug. I'll throw in a link when that's done.

Oh, wait, no, it's probably not a bug. From Debian's changelog I just realized that Lucid's upstream aptitude was from October 2008 (version 0.4.11.11) while Maverick's is from June 2010 (0.6.3). There's probably some intended change in behaviour going on. I'll investigate.

---

### Post by mc4man on 2010-10-11
It's actually the aptitude remove that causes though probably better to just keep at aptitude install, then remove as far as bug.(if one
(i believe it's advised not to mix apt-get and aptitude, though just to note - apt-get install, aptitude remove, then apt-get won't find either

Edit: though a day or so later (forgot to re-install gcc), aptitude suddenly 'found' the auto libs...

---

### Post by eeried on 2010-10-13
Hello there,

I hit this thread while trying to find out if synaptic uses apt-get or aptitude?

My second question is: wasn't aptitude pre-installed in Lucid?

I was under the impression aptitude was handled things better than apt-get but this is probably a rumour since by default apt-get is used at least by Ubuntu and by Debian-based #!Crunchbang.

:confused:

---

