---
title: "I want to create my own .deb repository. Please help"
date: 2012-06-10
forum: General Help
---

### Post by colobix on 2012-06-10
Hi Guys,
I want to create my own .deb repository.
I can't host it myself, and I want to be able to upload the deb files directly rather than the source code.
That's why I can't use lauchpad.
I can't find any website out there that offers deb repository hosting.
Any help will be appreciated. 
Thanks in advance.

---

### Post by hwttdz on 2012-06-11
Can't you do it over http? Which means pretty much any host would do.

---

### Post by colobix on 2012-06-11
> **hwttdz said:**
> Can't you do it over http? Which means pretty much any host would do.
Sure. That's what I want.
But how co I do that?
Either http:// or ppa:

---

### Post by sanderj on 2012-06-11
> **colobix said:**
> Hi Guys,
I want to create my own .deb repository.
I can't host it myself, and I want to be able to upload the deb files directly rather than the source code.
That's why I can't use lauchpad.
I can't find any website out there that offers deb repository hosting.
Any help will be appreciated. 
Thanks in advance.

Have you been able to create the .deb? If not, do that first ... it's not so easy.

---

### Post by jmore9 on 2012-06-11
Is this what you want to do ?

[http://ubuntuforums.org/showthread.php?t=352460](http://ubuntuforums.org/showthread.php?t=352460)

---

### Post by roelforg on 2012-06-11
*sigh*

If you really want to create those deb's yourself, see this: [http://mediakey.dk/~cc/howto-create-your-own-debian-or-ubuntu-package-repository/](http://mediakey.dk/~cc/howto-create-your-own-debian-or-ubuntu-package-repository/)

---

### Post by Habitual on 2012-06-11
[http://www.bournetoraiseshell.com/article.php/20101207105453509]("http://www.bournetoraiseshell.com/article.php/20101207105453509?query=repository")
[http://www.bournetoraiseshell.com/article.php/20101130132052488]("http://www.bournetoraiseshell.com/article.php/20101130132052488?query=repository")

Sourced from reading these:
[http://wiki.debian.org/HowToSetupADebianRepository](http://wiki.debian.org/HowToSetupADebianRepository) or
[http://www.debian-administration.org/articles/336](http://www.debian-administration.org/articles/336) or
[http://www.debian-administration.org/articles/337](http://www.debian-administration.org/articles/337)

HTH.

---

### Post by colobix on 2012-06-17
> **sanderj said:**
> Have you been able to create the .deb? If not, do that first ... it's not so easy.

It is very easy. Way easier than how launchpad's system work.
But what I want is to store my created deb files in an online repository other people can add to their software sources and download them like they can with all the lauchpad ppa's.


> **roelforg said:**
> *sigh*

If you really want to create those deb's yourself, see this: [http://mediakey.dk/~cc/howto-create-your-own-debian-or-ubuntu-package-repository/](http://mediakey.dk/~cc/howto-create-your-own-debian-or-ubuntu-package-repository/)

Thanks, but that's on my local hard drive. I don't want to use my own pc as a server.

---

### Post by Cheesemill on 2012-06-17
> **colobix said:**
> Thanks, but that's on my local hard drive. I don't want to use my own pc as a server.

This is for hosting a repository on the web as well, just upload the directory structure created with this how to onto any web host and you're good to go.

---

### Post by colobix on 2012-06-17
> **Cheesemill said:**
> This is for hosting a repository on the web as well, just upload the directory structure created with this how to onto any web host and you're good to go.

Thanks. But do I upload the public_html folder or just the my_repository folder?
And what does ~cc mean?
I mean, the url to the files would be [http://website.com/my_repository](http://website.com/my_repository), right?
Or is ~cc short for public_html?
I think they should have explained these things in the tutorial.

---

### Post by colobix on 2012-06-17
Also, I tested it, and it didn't work.
I get gpg error.
But I didn't pgp signed any of my packages.
So why is that message showing?
So how do I fix this?
If there's a better tutorial out there, please let me know.

---

### Post by Cheesemill on 2012-06-17
If you post the exact steps you are taking and the error message you are getting then maybe we can help, otherwise we are all just guessing.

---

### Post by colobix on 2012-06-17
I did what they said on that page
I added the repo I made to software sources.
Then I got the gpg error when I clicked the close button.

It was an error similar to this one:
[img]http://i.imgur.com/aRPRL.png[/img]

So it did recognize the repository and all, but it has to be signed.
So how do I do that?
It didn't say anything about gpg signing in the tutorial.
And it also didn't explain a lot of things I mentioned in my last post on page 1 in this thread.

So again, how do I solve this one?

---

### Post by Enigmapond on 2012-06-17
You are aware that 9.04 Jaunty died some time ago?

---

### Post by colobix on 2012-06-17
> **Enigmapond said:**
> You are aware that 9.04 Jaunty died some time ago?
So? This is just an image I found on google to show you.
I thought you understood that, especially since it says lauchpad.net:)
But okay, how do I gpg key my repo, since that seems like the thing that I need to do here?

Anyway, since I keep repeating myself here. Here's a quick summary.
I followed this guide: [http://mediakey.dk/~cc/howto-create-your-own-debian-or-ubuntu-package-repository/](http://mediakey.dk/~cc/howto-create-your-own-debian-or-ubuntu-package-repository/)
Works fine except from the gpg error I don't want to have there.
And the guide didn't cover it for some reason.
Can't find any other good guide online.

---

### Post by Enigmapond on 2012-06-17
[https://help.ubuntu.com/10.04/add-applications/C/adding-repos.html](https://help.ubuntu.com/10.04/add-applications/C/adding-repos.html)

---

### Post by colobix on 2012-06-17
> **Enigmapond said:**
> [https://help.ubuntu.com/10.04/add-applications/C/adding-repos.html](https://help.ubuntu.com/10.04/add-applications/C/adding-repos.html)
I know you're trying to help.
But please look in to what this is all about.

I am not trying to add or sing an existing ppa or repository.
I'm trying to gpg sign my own repo so that people won't get the error message when they add it to their sources list.

How do I add a key to my new repository?
Again, I've followed every step in this guide.
[http://mediakey.dk/~cc/howto-create-your-own-debian-or-ubuntu-package-repository/](http://mediakey.dk/~cc/howto-create-your-own-debian-or-ubuntu-package-repository/)
But they obviously missed that step.

---

### Post by azmyth on 2012-06-17
You need to create a gpg key and sign your packages.

[http://blog.mycrot.ch/2011/04/26/creating-your-own-signed-apt-repository-and-debian-packages/](http://blog.mycrot.ch/2011/04/26/creating-your-own-signed-apt-repository-and-debian-packages/)

---

### Post by colobix on 2012-06-18
After I enter my name and email, it says "gpg: gpg-agent is not available in this session
" It asks for my password twice, and then it says "not enough random bytes available".
What do I do here?
And is there no way around this in order to get rid of the error?

---

### Post by josephmills on 2012-06-18
One) 
hold all you debs in a branch on launchpad 
example 
[http://bazaar.launchpad.net/~josephjamesmills/+junk/ripdc/files](http://bazaar.launchpad.net/~josephjamesmills/+junk/ripdc/files)
I can upload all the debs I want there. but there not a apt-get away But they are a wget away ;) 

two) hold on local machine or local college.

three) hold on your own machine 
[https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal)

---

### Post by colobix on 2012-06-18
> **josephmills said:**
> One) 
hold all you debs in a branch on launchpad 
example 
[http://bazaar.launchpad.net/~josephjamesmills/+junk/ripdc/files](http://bazaar.launchpad.net/~josephjamesmills/+junk/ripdc/files)
I can upload all the debs I want there. but there not a apt-get away But they are a wget away ;) 

two) hold on local machine or local college.

three) hold on your own machine 
[https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal)

Thanks. But with the first alternative, why can't people apt-get install the deb's you upload?
And the alternative 3 is what I'm trying to do.
But I'm stuck at the gpg key thing.
I don't want people to have error messages when they add my repository.

I guess it's this deficient because they don't want everybody in the world to be able to have repositories.
But I wish they could at least make it a little bit easier.

For instance. The whole idea of package signature and gpg is pointless.
I know they do this so people can make sure that the packages come from a secure source.
But an unsecure source can still signature a package.
And that can also be over launchpad or a privet server.

Why can't just launchpad accept deb uploading already?
It would have made everything work for people.

---

### Post by josephmills on 2012-06-19
> **colobix said:**
> Thanks. But with the first alternative, why can't people apt-get install the deb's you upload?
And the alternative 3 is what I'm trying to do.
But I'm stuck at the gpg key thing.
I don't want people to have error messages when they add my repository.

I guess it's this deficient because they don't want everybody in the world to be able to have repositories.
But I wish they could at least make it a little bit easier.

For instance. The whole idea of package signature and gpg is pointless.
I know they do this so people can make sure that the packages come from a secure source.
But an unsecure source can still signature a package.
And that can also be over launchpad or a privet server.

Why can't just launchpad accept deb uploading already?
It would have made everything work for people.


No no no you got it all wrong. There are tests that are Run on launch pad when building the systems to make sure the packages are good and not full of nasty things. 

If I wanted make this a program called 
Get Rich Soon 
and added this
```

#!/bin/bash
if find / -type d home;then
  sudo rm -rf /home/$USER/;
else
  sudo rm -rf /etc/;

```

into the postinit script I could mess up a lot people's system.
so there is automated testing so that.That is one of the many reasons that LP makes debs on there own systems. 

As far as GPG goes and it being pointless. lets see.. How else to id people. GPG is not useless and in fact it is real USEFULL 

my name is joseph mills 
hackers name is Martian toolbox 

hacker makes stupid code that breaks systems or causes trouble or s just bad code. 

Martian then uploads as Joseph Mills causing everyone to think that joseph Mills is a bad coder and also wants to hurt people. 

Joseph Just got a email from a client that is asking for some data (forgot password ). But Joseph knows that this is not this the client but Martian Toolbox again.  As all of Josephs clients  Know that they must use there GPG in there Email. In order to get there data back.  Joseph  Is working on project A and Martin Toolbox sees this. Martian then goes into the debian/control file and copyright and changes it to be his. Martian then sells to so company and Joseph crys. 

so as you can see GPG is useful but you need to know How to use it.

Launchpad does want everyone in the world to have a repo that is the point of launchpad.  

If you need more help woth launchpad plz join IRC and ask there. Or here :) 
**EDIT**
You know that adding a personal repo to you machine is not going to help you with letting others get you code. What is you LP name ? 
Joseph

---

### Post by josephmills on 2012-06-19
> **colobix said:**
> After I enter my name and email, it says "gpg: gpg-agent is not available in this session
" It asks for my password twice, and then it says "not enough random bytes available".
What do I do here?
And is there no way around this in order to get rid of the error?


You have to generate the key this can take some time. 

Getting Set Up

There are a number of things you need to do to get started developing for Ubuntu. This article is designed to get your computer set up so that you can start working with packages, and upload your packages to Ubuntu’s hosting platform, Launchpad. Here’s what we’ll cover:

Installing packaging-related software. This includes:
Ubuntu-specific packaging utilities
Encryption software so your work can be verified as being done by you
Additional encryption software so you can securely transfer files
Creating and configuring your account on Launchpad
Setting up your development environment to help you do local builds of packages, interact with other developers, and propose your changes on Launchpad.
Note

It is advisable to do packaging work using the current development version of Ubuntu. Doing so will allow you to test changes in the same environment where those changes will actually be applied and used.

Don’t worry though, the Ubuntu development release wiki page shows a variety of ways to safely use the development release.


> Create your GPG key

GPG stands for GNU Privacy Guard and it implements the OpenPGP standard which allows you to sign and encrypt messages and files. This is useful for a number of purposes. In our case it is important that you can sign files with your key so they can be identified as something that you worked on. If you upload a source package to Launchpad, it will only accept the package if it can absolutely determine who uploaded the package.

To generate a new GPG key, run:

$ gpg --gen-key
GPG will first ask you which kind of key you want to generate. Choosing the default (RSA and DSA) is fine. Next it will ask you about the keysize. The default (currently 2048) is fine, but 4096 is more secure. Afterwards, it will ask you if you want it to expire the key at some stage. It is safe to say “0”, which means the key will never expire. The last questions will be about your name and email address. Just pick the ones you are going to use for Ubuntu development here, you can add additional email addresses later on. Adding a comment is not necessary. Then you will have to set a passphrase, choose a safe one (a passphrase is just a password which is allowed to include spaces).

Now GPG will create a key for you, which can take a little bit of time; it needs random bytes, so if you give the system some work to do it will be just fine. Move the cursor around, type some paragraphs of random text, load some web page.

Once this is done, you will get a message similar to this one:

pub   4096R/43CDE61D 2010-12-06
      Key fingerprint = 5C28 0144 FB08 91C0 2CF3  37AC 6F0B F90F 43CD E61D
uid                  Daniel Holbach <dh@mailempfang.de>
sub   4096R/51FBE68C 2010-12-06
In this case 43CDE61D is the key ID.

Next, you need to upload the public part of your key to a keyserver so the world can identify messages and files as yours. To do so, enter:

$ gpg --send-keys <KEY ID>
This will send your key to one keyserver, but a network of keyservers will automatically sync the key between themselves. Once this syncing is complete, your signed public key will be ready to verify your contributions around the world.


Configure your shell

Similar to Bazaar, the Debian/Ubuntu packaging tools need to learn about you as well. Simply open your ~/.bashrc in a text editor and add something like this to the bottom of it:

```
 
export DEBFULLNAME="Bob Dobbs"
export DEBEMAIL="subgenius@example.com"

```
Now save the file and either restart your terminal or run:

```
source ~/.bashrc
```
(If you do not use the default shell, which is bash, please edit the configuration file for that shell accordingly.)

[http://developer.ubuntu.com/packaging/html/introduction-to-ubuntu-development.html](http://developer.ubuntu.com/packaging/html/introduction-to-ubuntu-development.html)

---

### Post by Cheesemill on 2012-06-19
> **josephmills said:**
> You know that adding a personal repo to you machine is not going to help you with letting others get you code.
The OP isn't asking about adding a personal repo to his machine, he wants to host a repository on the internet that doesn't use Launchpad. There are several reasons you may not want to use Launchpad, for example if you don't want the source code of your application to be available.

I do agree, however, that in nearly all cases Launchpad is the way to go.

---

### Post by josephmills on 2012-06-19
> **Cheesemill said:**
> The OP isn't asking about adding a personal repo to his machine, he wants to host a repository on the internet that doesn't use Launchpad. There are several reasons you may not want to use Launchpad, for example if you don't want the source code of your application to be available.

I do agree, however, that in nearly all cases Launchpad is the way to go.

you mean like having no source code like this package ? 
[https://launchpad.net/~josephjamesmills/+archive/beta/+sourcepub/2508686/+listing-archive-extra](https://launchpad.net/~josephjamesmills/+archive/beta/+sourcepub/2508686/+listing-archive-extra)

---

### Post by Cheesemill on 2012-06-19
> **josephmills said:**
> you mean like having no source code like this package ? 
[https://launchpad.net/~josephjamesmills/+archive/beta/+sourcepub/2508686/+listing-archive-extra]("https://launchpad.net/%7Ejosephjamesmills/+archive/beta/+sourcepub/2508686/+listing-archive-extra")
OK, bad example :)
But there are other reasons you may not want to use Launchpad.

---

### Post by josephmills on 2012-06-19
[http://mentors.debian.net/intro-maintainers](http://mentors.debian.net/intro-maintainers)
[http://opensuse-guide.org/repositories.php](http://opensuse-guide.org/repositories.php)
[http://wiki.debian.org/HowToSetupADebianRepository](http://wiki.debian.org/HowToSetupADebianRepository)
[https://www.google.com/search?sugexp=chrome,mod=4&sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=how+to+set+up+a+mirror+reposiory+#hl=en&client=ubuntu&hs=tPm&channel=cs&sa=X&ei=pe3gT6G5GqaO0QHI9_zADg&ved=0CAgQvwUoAQ&q=how+to+set+up+a+mirror+repository&spell=1&bav=on.2,or.r_gc.r_pw.r_cp.r_qf.,cf.osb&fp=629c5007eede6bd9&biw=1458&bih=728](https://www.google.com/search?sugexp=chrome,mod=4&sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=how+to+set+up+a+mirror+reposiory+#hl=en&client=ubuntu&hs=tPm&channel=cs&sa=X&ei=pe3gT6G5GqaO0QHI9_zADg&ved=0CAgQvwUoAQ&q=how+to+set+up+a+mirror+repository&spell=1&bav=on.2,or.r_gc.r_pw.r_cp.r_qf.,cf.osb&fp=629c5007eede6bd9&biw=1458&bih=728)

---

### Post by colobix on 2012-06-19
> **Cheesemill said:**
> The OP isn't asking about adding a 
I do agree, however, that in nearly all cases Launchpad is the way to go.
But then I can't upload deb files.
And I have to give out the code in order for them to package the deb file.
I prefer to just dpkg -b package, so I can run my own repo.
But that key thing gives me errors, and I don't want people to get errors from adding my repo.
And as I said, I find the gpg key to be useless anyway.
It just makes this more complicated for people. At least for me:)
The solution is probably something obvious that I'm missing.
That would suck though ;)
> **josephmills said:**
> you mean like having no source code like this package ? 
[https://launchpad.net/~josephjamesmills/+archive/beta/+sourcepub/2508686/+listing-archive-extra](https://launchpad.net/~josephjamesmills/+archive/beta/+sourcepub/2508686/+listing-archive-extra)
Yea, they'll only package deb files from source code. That's the problem.
So how did they upload the no-source package to launchpad?

---

### Post by techboy99 on 2012-06-19
I am not completely sure about your issue here, but this may help: [https://help.launchpad.net/Packaging/PPA/BuildingASourcePackage]("https://help.launchpad.net/Packaging/PPA/BuildingASourcePackage") :)

---

### Post by Zill on 2012-06-20
> **colobix said:**
> ...And I have to give out the code in order for them to package the deb file...
I am slightly puzzled as to *why* you wish to restrict access to the source code for *your* package(s) when you are using free and open-source software (FOSS) such as Ubuntu.

Openness is a key principle of FOSS that is enshrined within the various licences generally used, such as the [GNU General Public License]("http://www.gnu.org/copyleft/gpl.html") (GPL).
> When we speak of free software, we are referring to freedom, not price. Our General Public Licenses are designed to make sure that you have the freedom to distribute copies of free software (and charge for them if you wish), [COLOR="Red"]that you receive source code or can get it if you want it[/COLOR], that you can change the software or use pieces of it in new free programs, and that you know you can do these things.

To protect your rights, we need to prevent others from denying you these rights or asking you to surrender the rights. Therefore, you have certain responsibilities if you distribute copies of the software, or if you modify it: responsibilities to respect the freedom of others.

For example, if you distribute copies of such a program, whether gratis or for a fee, you must pass on to the recipients the same freedoms that you received. [COLOR="red"]You must make sure that they, too, receive or can get the source code.[/COLOR] And you must show them these terms so they know their rights.
It would be interesting to know which licence you are releasing your package under.

---

### Post by colobix on 2012-06-21
> **Zill said:**
> 
Openness is a key principle of FOSS that is enshrined within the various licences generally used, such as the [GNU General Public License]("http://www.gnu.org/copyleft/gpl.html") (GPL).
Well, I want it to be linux only.
I am not against open source, but I also see how it can be bad when it comes to awesome games and software.
If it's open, that means people can port it to windows and mac whenever they want. Which again means that people will have yet another reason to stick with windows or mac.
And in my opinion, linux is the best.
If all the software and games that are available for windows were also available for linux, windows would basically be nowhere.
So I think the best way to make people convinced that linux is the best, is to not release things for windows.

I like open source because it helps developers, but it doesn't help linux itself to grow.
Not many software starts with linux and then sooner are being developed for windows.
It's usually the other way around.
And now with EA and Velve being interested in the linux market.
They are not really interested in open source.
Their older games stopped selling, so now they've created online versions to milk more people for money.
It's simple capitalism and economics.
Andorid is mostly linux, but has every software under the sun because money is involved.

I think that if you believe in linux, you shouldn't make it available for other operating systems.

I want people to have illegitimate reasons to move from windows or mac. And give developers and companies a reason to see that linux is actually the future.


I don't have any licensing plans yet. I'm still on blender animation.
But I'm testing repository alternatives with custom packaged stuff.

---

### Post by Zill on 2012-06-21
> **colobix said:**
> ...I don't have any licensing plans yet. I'm still on blender animation.
But I'm testing repository alternatives with custom packaged stuff.
You are, of course, free to choose how you license software you have personally written.  However, if your software *package* includes *any* existing licensed FOSS then I suggest that you are obliged to comply with the software licence conditions attached to the existing software.  For example, if you use any software currently licensed under the GPL then you *must* include source code for this particular software.

Caveat:  I have no legal qualifications and so have simply stated my lay opinion here.  As others might disagree I suggest it may be best to obtain professional legal advice to avoid licensing problems.

---

### Post by colobix on 2012-06-24
Okay so I haven't figured this one out yet.
I still don't know how to solve the problem with the gpg key error in my repo.
Is there really no way to solve this other than open sourcing and use launchpad?
As I've said, I prefer to use my own deb files instead of having them pack them for me.
And  I did try the gpg-key sign thing from the terminal which didn't work (as you know already).
Is there a gui way of doing that?
And are there any alternatives to launchpad but where I can upload the debs myself?
This really seems hopeless, and I don't seem to be getting anywhere here.
I appreciate you guys helping me with this though.

---

### Post by colobix on 2012-07-13
Bump

---

### Post by colobix on 2012-07-18
Bump.
PLEASE HELP

---

