---
title: "What are recommended programs for Ubuntu?  Or sites that have a list of some?"
date: 2011-09-04
forum: General Help
---

### Post by pretty_whistle on 2011-09-04
When I had Windows I could go to download.com (CNET) and see lists of reviewed programs and recommended ones.  Does such a thing exist for Ubuntu or Linux?  Are there any websites like this?

I already know Ubuntu Software Center has programs with ratings but what I'm wondering about is if there are* websites *like this (as I said).

---

### Post by IWantFroyo on 2011-09-04
There are Ubuntu blogs that specialize in stuff like this:
[www.omgubuntu.co.uk](www.omgubuntu.co.uk)
[www.webupd8.org](www.webupd8.org)

Also, a lot of forum users keep blogs of their own.

Just do your research before installing. Google the name of the app to see how trustworthy it is, and check out the Software Center to see if it's there. If you can, try to find a ppa instead of installing the .deb.

---

### Post by spiky001 on 2011-09-04
Have a look in the software centre, Which is part of your install, It will have most things you want and is safe software. Sourceforge is web site for software as well, Try to stick to software centre

---

### Post by pretty_whistle on 2011-09-04
> **IWantFroyo said:**
> There are Ubuntu blogs that specialize in stuff like this:
[www.omgubuntu.co.uk]("http://www.omgubuntu.co.uk")
[www.webupd8.org]("http://www.webupd8.org")

Also, a lot of forum users keep blogs of their own.

Just do your research before installing. Google the name of the app to see how trustworthy it is, and check out the Software Center to see if it's there. If you can, try to find a ppa instead of installing the .deb.

Excuse my noob-ness but what  is ppa and .deb?

---

### Post by IWantFroyo on 2011-09-04
A ppa is a repository hosted on LaunchPad (the Ubuntu development website).
You add a ppa with:
```
sudo add-apt-repository ppa:theppa/something
```
```
sudo apt-get update
```
This then lets you install the package with apt-get, Synaptic, or the Software Center.

A .deb is sort of the Ubuntu equivalent of a .exe. You double click on it, and install it via the software center. Deb files aren't always trustworthy, and you can't update them through apt-get or the Update Manager.

PPAs are just superior and safer than installing by .deb.

---

### Post by spiky001 on 2011-09-04
Try not to get involved with .tar files, These take abit of installing.

---

### Post by haqking on 2011-09-04
here are a few useful links

[http://blog.sudobits.com/2011/03/19/top-10-ubuntu-apps/](http://blog.sudobits.com/2011/03/19/top-10-ubuntu-apps/)

[http://blog.sudobits.com/2011/03/07/top-10-ubuntu-games/](http://blog.sudobits.com/2011/03/07/top-10-ubuntu-games/)

[http://www.programmerfish.com/top-10-apps-that-boosts-ubuntus-user-experience/](http://www.programmerfish.com/top-10-apps-that-boosts-ubuntus-user-experience/)

[http://www.makeuseof.com/tag/10-applications-install-ubuntu-lucid-lynx/](http://www.makeuseof.com/tag/10-applications-install-ubuntu-lucid-lynx/)

I wouldnt necessarily agree with all the choices, but thats the beauty of Linux as everything is choice ;-)

Enjoy

---

### Post by pretty_whistle on 2011-09-04
> **spiky001 said:**
> Try not to get involved with .tar files, These take abit of installing.

I noticed!

---

### Post by IWantFroyo on 2011-09-04
> **pretty_whistle said:**
> I noticed!

Tar files aren't very good ways to install stuff. If something tells you you have to install through a .tar, then either there's an easier way (Google the program, the version of Ubuntu, and 'ppa'), or the program isn't really trustworthy enough (at least to me) to install.

In other words, do research, and stay away from tar files.

---

### Post by pretty_whistle on 2011-09-04
> **spiky001 said:**
> Try not to get involved with .tar files, These take abit of installing.

Although, I've installed .tar.bz2 without trouble.

---

### Post by pretty_whistle on 2011-09-04
> **IWantFroyo said:**
> Tar files aren't very good ways to install stuff. If something tells you you have to install through a .tar, then either there's an easier way (Google the program, the version of Ubuntu, and 'ppa'), or the program isn't really trustworthy enough (at least to me) to install.

In other words, do research, and stay away from tar files.

I've made a note of that.

---

### Post by haqking on 2011-09-04
.tar files are nothing to be scared of, though to the uninitiated they can be daunting.

first of all a .tar file is merely a packaging/distribution format much like a .zip file in windows.

There contents needs to be extracted thats all. see here [https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression) (alot of the time it is simply a case of right clicking in nautilus and choosing extract and your are done)

you get comfortable with them after a while.

I think where the scary part or unfamiliar part comes is compiling from source which is generally how software comes when packaged as a .tar. Though often a .tar will simply contain a .deb file for easy installation.

depending on the documentation with the source it can be easy or a nightmare for sure.

See here [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo), even if you dont use compiling from source often it is a good skill to have.

.tar and compiling have there place.

but as mentioned always try to see if the software is available in the repos/ppa etc or a .deb from the software webpage.

Enjoy

---

### Post by IWantFroyo on 2011-09-04
> **haqking said:**
> .tar files are nothing to be scared of, though to the uninitiated they can be daunting.

first of all a .tar file is merely a packaging/distribution format much like a .zip file in windows.

There contents needs to be extracted thats all. see here [https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

you get comfortable with them after a while.

I think where the scary part or unfamiliar part comes is compiling from source which is gnerally how software comes when packaged as a .tar. Though often a .tar will simply contain a .deb file for easy installation.

depending on the documentation with the source it can be easy or a nightmare for sure.

See here [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo), even if you dont use compiling from source it is a good skill to have.

.tar and compiling have there place.

but as mentioned alwasy try to see if the software is available in the repos/ppa etc or a .deb from the software webpage.

Enjoy

If a tar comes with a .deb, then it's okay. What you want to stay away from is the complex stuff (you just get a bunch of folders and a .sh file) or compiling from source.

---

### Post by haqking on 2011-09-04
> **IWantFroyo said:**
> If a tar comes with a .deb, then it's okay. What you want to stay away from is the complex stuff (you just get a bunch of folders and a .sh file) or compiling from source.

I understand it can seem daunting and always recommend that people use software centre or similar.

fact is sometimes you cant, but its not that hard.  The [how to]("https://help.ubuntu.com/community/CompilingEasyHowTo") i posted is pretty concise, and if not most extracted .tar files have a readme or install text file giving you instructions on what to do which is usually copying and pasting a few commands into the terminal.

LIke i said im not saying it is easy as software centre but IMO not complex either, complex would be no instructions, most of the time there are some.

---

### Post by apollothethird on 2011-09-04
> **pretty_whistle said:**
> Although, I've installed .tar.bz2 without trouble.

As some has mentioned to you, tar files are not taboo, as your message seems to suggest you interpreted.  .tar.bz2 files fall under the same category.  The difference between the tar files and the tar.bz2 files you mentioned is the compression.  Many times you can find the exact files compressed under tar or compressed under tar.bz2.  Once opened, you'll see the same files.  So if you've worked with tar.bz2, you've basically worked with tar files.

There's nothing wrong with tar files except for the fact that they might not necessarily have gone through a lot of testing by the community.  If you're working with a trustworthy source where you can get support, it might not be much difference.

The main this is that the files you find in the repos have been tested by the community and are very likely safe.

People have lots of problems with Windows because they browse sites and download zip files that haven't gone through the scrutiny of the Linux packages.

There are over 30 thousand programs in the Ubuntu repository and many more than that in the Debian repository.  If you take a consideration of what you actually want to do, just type in the search bar of the Software Center and you'll probably find something tested by the community to do a pretty good job.

If you are looking for something specific and don't find something in the repository to fit the build, give a description to the community.  Chances are you won't be the first who looked for such a program.  You'd most likely get lots of great suggestions from programs that have been tested by the community.

You might invite problems and have a hard time getting support for fixing some of them if you decide to start outside the box rather than inside the box.

Personally, I'd start browsing and exploring the 10's of thousands of programs already provided.  A person might not have time to go outside and risk malware with this method.  It'd take a very long time to go over all the programs.

By the way, I'm not telling you not to go out and test all the other programs outside the box.  Someone has to test them and find out what type of problems if any they can present.  If they are safe, maybe you can introduce new programs to the community.

In short, I believe you've already named the counterpart for Ubuntu software, as post to the Windows site.  The counterpart is the Software Center.  I'd be interested in your experience with it, and where it falls short.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by spiky001 on 2011-09-04
Thanks IWantFroyo, haqking, and apollothethird for explain tar files/source you explained it better than me I,m glad i pointed tar files out

---

### Post by debd on 2011-09-04
[http://linuxappfinder.com/all](http://linuxappfinder.com/all)

---

### Post by pretty_whistle on 2011-09-04
Interesting what everyone has to say.

Now that I think about it I've installed .tar as well.

I have a method I use to install such files but I wouldn't say this is the 'how to' others would propose on the topic.  What I do is make a desktop folder called "programs", extract the .tar or .tar.bz2 there, then create a launcher to the file in the extracted folder that executes said program.  I've installed Seamonkey and Thunderbird email programs this way.  It was quite easy to do IMO.

I may have been able to get Seamonkey and Thunderbird via the Software Center but I didn't think of looking there.  No biggie though since I actually find installing via the method I just mentioned kinda fun. :)

And thanks for all the sites you've all given.  That'll help alot.

Edit:  I also like looking all over for programs and not being confined to the Software Center.

---

### Post by haqking on 2011-09-04
> **pretty_whistle said:**
> Interesting what everyone has to say.

Now that I think about it I've installed .tar as well.

I have a method I use to install such files but I wouldn't say this is the 'how to' others would propose on the topic.  What I do is make a desktop folder called "programs", extract the .tar or .tar.bz2 there, then create a launcher to the file in the extracted folder that executes said program.  I've installed Seamonkey and Thunderbird email programs this way.  It was quite easy to do IMO.

I may have been able to get Seamonkey and Thunderbird via the Software Center but I didn't think of looking there.  No biggie though since I actually find installing via the method I just mentioned kinda fun. :)

And thanks for all the sites you've all given.  That'll help alot.


Edit:  I also like looking all over for programs and not being confined to the Software Center.

You wont be creating a launcher to compile from source ;-)

---

### Post by pretty_whistle on 2011-09-04
> **haqking said:**
> You wont be creating a launcher to compile from source ;-)

I'm aware of that.

When I had Windows 7 (yuk! :) ) I made a program in Basic and didn't have to create anything like that to get it to run.

Working with source will be interesting and fun.  I'll put that on my list to do.  :p

---

### Post by texaswriter on 2011-09-04
This is a great website with a list of proprietary website and some open source equivalents listed below. 

It also houses a list of open source software by itself as well. 

Check it out!!

[www.osalt.com ]("http://www.osalt.com")

---

### Post by PayPaul on 2011-09-18
Hm. Hmmm. Tar files? Yeah I encountered one that gave me a very sinking feeling. Like an Elephant from La Brea.

What are the risks of these more untrustworthy files. I mean, it's been said in a lot of places that Ubuntu and Linux are just about immune from viruses and malware.

I'm looking for a good file and folder search app and can't find any that are adequate or well recommended. I have to say that the native search program in Ubuntu 11 sucks eggs. It takes longer to find things than my Windows program, Everything.

---

### Post by texaswriter on 2011-09-18
> **PayPaul said:**
> Hm. Hmmm. Tar files? Yeah I encountered one that gave me a very sinking feeling. Like an Elephant from La Brea.

What are the risks of these more untrustworthy files. I mean, it's been said in a lot of places that Ubuntu and Linux are just about immune from viruses and malware.

I'm looking for a good file and folder search app and can't find any that are adequate or well recommended. I have to say that the native search program in Ubuntu 11 sucks eggs. It takes longer to find things than my Windows program, Everything.

No operating system is immune to viruses and malware. Linux's transparency helps bugs and vulnerabilities get resolved faster, but only if people report bugs. That said, if you a user installs something malicious, than that is unavoidable on any operating system as well.

---

