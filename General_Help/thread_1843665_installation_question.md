---
title: "installation question"
date: 2011-09-13
forum: General Help
---

### Post by mattpl1981 on 2011-09-13
my laptop is a 64 bit system but while installing it has an optipn of choosing 32 and 64 bit and it recommends 32 bit. im asking should i choose 32 bit even though my system is 64??

---

### Post by haqking on 2011-09-13
> **mattpl1981 said:**
> my laptop is a 64 bit system but while installing it has an optipn of choosing 32 and 64 bit and it recommends 32 bit. im asking should i choose 32 bit even though my system is 64??


If you have x64 then install 64 bit.  it defaults to recommending 32bit.

If you have 2GB or less RAM though you might consider 32 bit or x64 and get some more memory to take advantage.

Try the live CD first without installing to check that x64 works fine.

---

### Post by mattpl1981 on 2011-09-13
ok thanks i have 4 GB ram so i think ill be fine

---

### Post by Dr. Nick on 2011-09-13
It may be better now, but several years ago when I was using 64bit many of the programs were not compiled for 64bit so 32bit was recommended from an ease of use standpoint. Like I said that was several years ago so its probably better now, still something to keep in mind though

---

### Post by haqking on 2011-09-13
> **mattpl1981 said:**
> ok thanks i have 4 GB ram so i think ill be fine


I run x64 with 4Gb and everything is fine.  I run virtual machines both 32 bit and 64 bit on my 64 bit host also and no problems.

I suspect the most common issue people experience is Flash. as x64 for Linux is still in beta (works fine though)

however you might take a look at [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/")

I suggest using [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/") for firefox, as it will download the best version for your system and can use across browsers once installed.

usually solves about 99.9%of Flash issues posted on this forum, it was created by one of the community members (lovinglinux)

hope this helps

regards

haqking

---

### Post by rhapa on 2011-09-13
Although it is better for you to use 64 bit OS since you have 4gb of ram you really should think about using the 32bit (i386) version since it run as smooth as the 64bit. Why would it be? Well, because a lot of programs aren't compatible with 64bit and it'll be such a headache to manage apps to run properly or to install easily the 64bit version of the app. If you're new in the linux world for sure you shall take the i386 version. 

I.e.: to install adobe flash in 64bit you have to use source codes, which is hard for beginners. Automatic packages (such as .deb or .run or .rpm) aren't available for 64bit version of Ubuntu.

My system is 64bit and run both i386 and 64bit versions of Ubuntu and I've to say that there's a lot more of apps available of the i386 version.

---

### Post by haqking on 2011-09-13
> **rhapa said:**
> Although it is better for you to use 64 bit OS since you have 4gb of ram you really should think to use the 32bit (i386) version since it run as smooth as the 64bit. Why would it be? Well, because a lot of programs aren't compatible with 64bit and it'll be such a headache to manage apps to run properly or to install easily the 64bit version of the app. If you're new in the linux world for sure you shall take the i386 version. 

I.e.: to install adobe flash in 64bit you have to use source codes, which is hard for beginners. Automatic packages (such as .deb or .run or .rpm) aren't available for 64bit version of Ubuntu.


thats not true, you dont have to install flash from source code manually.

see my post above.

also i havent found an app that doesnt work on x64 yet.  Can you point me to one ? I mean im not saying there arent any, i mean point me to one as everything works fine on mine.

---

### Post by drs305 on 2011-09-13
I agree with *haqking*. I've used 64-bit Ubuntu for many years and there have been great improvements. Flash problems are much rarer now and Flash Aid is a great tool.

I really don't have to even think much about adapting for 64-bit any longer; any 64-bit issues seem to take care of themselves during installation.

---

### Post by oldos2er on 2011-09-13
> **rhapa said:**
> My system is 64bit and run both i386 and 64bit versions of Ubuntu and I've to say that there's a lot more of apps available of the i386 version.

I can only think of two, Skype and acroread, and both of those will run on a 64-bit system with ia32-libs installed.

---

### Post by rhapa on 2011-09-13
> **haqking said:**
> thats not true, you dont have to install flash from source code manually.

see my post above.

also i havent found an app that doesnt work on x64 yet.  Can you point me to one ? I mean im not saying there arent any, i mean point me to one as everything works fine on mine.

For sure you're right, you don't have to install flash manually. When I said that I was thinking about people who are new to linux (as I was then). Usually to install flash if you haven't installed it during the OS installation (which is easily possible now) you'd have to install from the repositories with terminal, from Ubuntu Software Center, from the plugin finder in Firefox or directly from Adobe. As said nouveau people usually don't know this and if the firefox plugin finder fails to install Flash or etc. you'd probably get it direct from adobe. If you're running a 64bit system the Adobe site doesn't give you the automatic package so you'll have to use the sources. That was what I meant.

When I told about the incompatibility problem, as because of you I see know, I was kind of wrong. It's because when I tried to move to 64bit first I didn't found the programs I used in 64bit versions (well, I actually found a little of them later, but after hard Googling). I saw your comments and I decided to login in my 64bit version to verify and guess what, all program that wasn't support in 64bit now has a version for it (save some old ones that are no longer in use or are useless nowadays) or you can manage to run them. Yeah, I must've said I was outdated...

Sorry my mistake....

---

### Post by BlacqWolf on 2011-09-13
> **oldos2er said:**
> I can only think of two, Skype and acroread, and both of those will run on a 64-bit system with ia32-libs installed.

Well, Skype also has a native 64-bit version so that's not really a problem.

And, isn't there going to be some way to run any 32-bit edition of a application on a x64 system without additional packages, like you can in Windows?

---

### Post by haqking on 2011-09-13
> **rhapa said:**
> For sure you're right, you don't have to install flash manually. When I said that I was thinking about people who are new to linux (as I was then). Usually to install flash if you haven't installed it during the OS installation (which is easily possible now) you'd have to install from the repositories with terminal, from Ubuntu Software Center, from the plugin finder in Firefox or directly from Adobe. As said nouveau people usually don't know this and if the firefox plugin finder fails to install Flash or etc. you'd probably get it direct from adobe. If you're running a 64bit system the Adobe site doesn't give you the automatic package so you'll have to use the sources. That was what I meant.

When I told about the incompatibility problem, as because of you I see know, I was kind of wrong. It's because when I tried to move to 64bit first I didn't found the programs I used in 64bit versions (well, I actually found a little of them later, but after hard Googling). I saw your comments and I decided to login in my 64bit version to verify and guess what, all program that wasn't support in 64bit now has a version for it (save some old ones that are no longer in use or are useless nowadays) or you can manage to run them. Yeah, I must've said I was outdated...

Sorry my mistake....


No problem, i see your point about being a new user etc.

But as others have said also, there are no real concerns nowadays. if you have the hardware choose x64 IMO

;-)

peace

---

### Post by rhapa on 2011-09-13
> **haqking said:**
> No problem, i see your point about being a new user etc.

But as others have said also, there are no real concerns nowadays. if you have the hardware choose x64 IMO

;-)

peace

You sure have opened my eyes. Thanks....

---

### Post by oldos2er on 2011-09-13
> **BlacqWolf said:**
> Well, Skype also has a native 64-bit version so that's not really a problem.

And, isn't there going to be some way to run any 32-bit edition of a application on a x64 system without additional packages, like you can in Windows?

I have no idea. In earlier versions of Ubuntu (than 10.10, I think?) ia32-libs was installed automatically.

Didn't know about Skype, thanks.

---

