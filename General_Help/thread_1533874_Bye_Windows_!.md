---
title: "Bye Windows !"
date: 2010-07-18
forum: General Help
---

### Post by 1Michael1 on 2010-07-18
So I'm going to delete Windows permanently from my laptop now.
But I've a couple of concerns that I'd like to be sort out before doing so.

1. Can I add myself into a domain after creating the user? It works great now, but in school I'm assigned to their domain (With my Windows user) and only the ones in the domain has internet access. So I'd like to know if I could create an user now (In Ubuntu) and when going back to school again in August they could simply add me into the domain somehow.

2. More or less everytime I download something it comes with the paddlock on the files. Could I set it to permenently unlock all these files on my pc? Like just whenever I get some music down or whatever the paddlock comes automaticly on it and I've to go change it with chmod or gksudo nautilus (Don't know the difference between those two commands), so is there some way to set it permenently so I don't have to change it everytime I turn on the box?

3. On Windows I've got Bitdefender that blocks everytime someone tries to do a scan on me through Nessus, is there some other great Firewall/AV like that which could block port scans, vulnerability scans etc on Ubuntu? Windows has some synfloods tweaks as well, where do Ubuntu stand on that, is that somehow built into the system or can it be done manually if not? I've already got TCP Syn cookies enabled. (I've hosted a bunch of servers earlier and been dealing with bunch of dos attacks so you can't blame me for being a bit paranoid, I'd like to have the best protection possible).

4. I'm the webmaster of a professional site and unfortunately a lot of people who is visiting the site are using IE so I've to make the site compatible with IE as well as other browsers. So is there some version of IE available, maybe through wine somehow? I've tried the Mozilla User Agent Switcher plugin which didn't work and IE 4 Linux didn't seem to work either.

**So that's my questions, to keep it in a short version;**

1. Add my user into a school domain to be able to use the internet.

2. Remove paddlocks permanently.

3. Best security protection for Ubuntu.

4. IE in Ubuntu.

If you don't want to go into detail just please, point me in the right direction by telling me that it either works or not and if it works, please provide me by giving me a tip or posting a link and I'll carry on reading further on my own.

Thanks a lot in advance,
Michael.

---

### Post by Marlonsm on 2010-07-18
Just set up a dual boot (very easy to do), so you'll have both Ubuntu and Windows, in case something goes wrong.

---

### Post by davidmohammed on 2010-07-18
that's a lot of questions - maybe one thread each would have been better.

- there isn't a IE for linux.  Given that you have to maintain compatibility - you are better off running a virtual XP guest in, for example, virtual box.

---

### Post by v1ad on 2010-07-18
the school should either use your mac address or have a web login so you should be fine.

for security look for firestarter.

not sure what you mean by padlock. i don't have any issues with that.

try the user agent switcher in chromium.

---

### Post by davidmohammed on 2010-07-18
...v1ad beat me to the answer

---

### Post by 1Michael1 on 2010-07-18
> **Marlonsm said:**
> Just set up a dual boot (very easy to do), so you'll have both Ubuntu and Windows, in case something goes wrong.

Well I do that atm, but my Windows box seems to run slower and slower after everytime so therefore I just wanted to get rid of it and save some disk space.

---

### Post by lkjoel on 2010-07-18
For the BitDefender Part, you can download it for free, and it will work on Linux.
Actually, the only free download is for Linux... another reason get Linux.

---

### Post by 1Michael1 on 2010-07-18
Yeah, it's awesome that they provide a free Linux version but it ain't as full featured as the Windows version which is sadly.

The fact why I don't actually want to run Windows as a dual boot is also because it's a mental problem while learning. If you bump into a problem in Ubuntu as a beginner, instead of trying to find solutions to make it work you just skip to Windows. But if I don't have any safe net around me I'd force myself to look for the solution. Not that Ubuntu would be much harder, the thing is that you need to put some time down when learning something, anything.

So anyone with some more suggestions? The domain problem seems to be able to work I believe but the IE problem would be amazing if it could be fixed somehow since I believe a lot of other guys has been in mine situation since a lot users visiting websites are running IE and therefore we're forced to make our site IE compatible, but it's hard to do it blindfolded.

---

### Post by the8thstar on 2010-07-18
You can always set a Virtual Machine with any version of Windows with VirtualBox and your Windows OS CDs/DVD. This is a good way to keep Internet Explorer running in a Windows environment while having the security of Ubuntu.

---

### Post by lkjoel on 2010-07-18
> **1Michael1 said:**
> Yeah, it's awesome that they provide a free Linux version but it ain't as full featured as the Windows version which is sadly.

The fact why I don't actually want to run Windows as a dual boot is also because it's a mental problem while learning. If you bump into a problem in Ubuntu as a beginner, instead of trying to find solutions to make it work you just skip to Windows. But if I don't have any safe net around me I'd force myself to look for the solution. Not that Ubuntu would be much harder, the thing is that you need to put some time down when learning something, anything.
I would completely agree with you.
Ubuntu takes some time to learn, but once you have learned it, you can power use it, and you don't have to learn any other systems. (Unless you are a cross-platform programmer)

---

### Post by v1ad on 2010-07-18
[https://chrome.google.com/extensions/detail/aafciojnlamllgpkpdkbamkfgbofhgcj](https://chrome.google.com/extensions/detail/aafciojnlamllgpkpdkbamkfgbofhgcj)

---

### Post by 1Michael1 on 2010-07-18
Thanks v1ad but unfortunately that seems to only work with specific websites.

---

### Post by 1Michael1 on 2010-07-19
Well concerning the domain issue, I might have to install Samba since the schools uses Windows. Don't you think so?

---

### Post by The Cog on 2010-07-19
Some places use a windows based proxy that won't allow users through unless they're registered on the windows domain. Microsoft are pushing this of course, and gullible IT staff just do whatever MS says they should. "Just keep shovelling the money over, suckers!" 

I'm not sure, but maybe winbind from the samba suite will register in the domain for you?

---

