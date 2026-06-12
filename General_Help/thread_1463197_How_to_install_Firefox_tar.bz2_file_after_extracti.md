---
title: "How to install Firefox tar.bz2 file after extracting"
date: 2010-04-26
forum: General Help
---

### Post by Riffronan on 2010-04-26
Hey there Folks...I'm pretty noob-ish but I did manage to right-click the Firefox tar.bz2 file and choose to 'extract here'...now I've got the new extracted folder on the desktop but I'm lost as to how to run the installation of the 3.7 alpha 4 release.  Any help would greatly be appreciated (!)  

9.10 Wubi with XP until 10.04
Google Chrome
Widmer Drifter Pale Ale
Tommyknocker Pick Axe Pale Ale
1992 Davies Washburn N4 w/ Suhr SSV/DSH+ pups
Jazz and Prog Rock, Dream Theatre & Porcupine Tree
  (I couldn't fit it all on my license plate so...)

   Thanks !  :guitar:

---

### Post by overlordchin on 2010-04-26
change directory into the folder it extracts. Generally there is a configure file in there. If there is type "./configure" 
That will create a make file. Then you will need to type "make"
and then "sudo make install"
Which will put everything in the appropriate folders.
If it fails you might be missing a package called "build-essentials" which you can get through apt-get

Hope that helps.:)

---

### Post by VCoolio on 2010-04-26
With firefox you can probably just run the firefox executable from within that folder; also search these forums for lovinglinux, he has some threads on how to install firefox versions on ubuntu.

---

### Post by lovinglinux on 2010-04-27
> **overlordchin said:**
> change directory into the folder it extracts. Generally there is a configure file in there. If there is type "./configure" 
That will create a make file. Then you will need to type "make"
and then "sudo make install"
Which will put everything in the appropriate folders.
If it fails you might be missing a package called "build-essentials" which you can get through apt-get

Hope that helps.:)

No, no, no. Just because a file is a tar.bz2 it doesn't mean it needs to be compiled. Mozilla releases both source code and ready-to-run binaries as tar.bz2. The only difference is that the one that needs to be compiled has ".source." included in the file name. The OP doesn't specify, but most likely he/she got the ready-to-run binaries and just want to launch Firefox. Anyway, when we are not sure about which file the user has, is better to ask first instead of giving compiling commands. Besides, compiling Firefox is not that simple, although it is not a nightmare. [See info here](http://lovinglinux.megabyet.net/?page_id=220#Compiling-Firefox-1).

> **VCoolio said:**
> With firefox you can probably just run the firefox executable from within that folder; also search these forums for lovinglinux, he has some threads on how to install firefox versions on ubuntu.

Indeed :)

See the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Installing-Other-Versions-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by overlordchin on 2010-04-27
> **lovinglinux said:**
> No, no, no. Just because a file is a tar.bz2 it doesn't mean it needs to be compiled. Mozilla releases both source code and ready-to-run binaries as tar.bz2. The only difference is that the one that needs to be compiled has ".source." included in the file name. The OP doesn't specify, but most likely he/she got the ready-to-run binaries and just want to launch Firefox. Anyway, when we are not sure about which file the user has, is better to ask first instead of giving compiling commands. Besides, compiling Firefox is not that simple, although it is not a nightmare. 


I could not remember if it needed to be compiled or not. You are right in this particular instance it is much more difficult to find the source tarball than the binary version (IE the primary download is binary and you actually have to look for the source package) In any case please do not criticize suggestions. If the OP has trouble with a suggestion or it does not work they will post for additional guidance or direction.

---

### Post by lovinglinux on 2010-04-27
> **overlordchin said:**
> In any case please do not criticize suggestions. If the OP has trouble with a suggestion or it does not work they will post for additional guidance or direction.

Sorry, but I disagree.

---

### Post by aysiu on 2010-04-27
I also disagree. In 99.9999% of cases in which people want to know how to "install" Firefox from the .tar.bz2, the compressed file contains a precompiled binary and not source code.

---

### Post by Riffronan on 2010-04-27
Thanks for the suggestions...I even tried to make sure the right libraries were in place..Mozilla's development center says to :

apt-get build-dep firefox

apt-get install mercurial libasound2-dev libcurl4-openssl-dev libnotify-dev libxt-dev libiw-dev mesa-common-dev autoconf2.13

but everytime I do the  ./configure, I get a configure: error: --enable-application=APP was not specified and is required...as a last entry..so I'm still working on it

---

### Post by overlordchin on 2010-04-27
This guy had the same problem as you:

[http://www.errorhelp.com/search/details/81771/error-enable-application-app-was-not-specified-and-is-required]("http://www.errorhelp.com/search/details/81771/error-enable-application-app-was-not-specified-and-is-required")

I am not sure what the  .mozconfig is that he mentions. Perhaps one of these other bright fellows know the answer.

this page says something diff: [http://mmszuto.blogspot.com/2007/09/building-firefox.html]("http://mmszuto.blogspot.com/2007/09/building-firefox.html")

he suggests you just need to add the argument it is complaining about to your ./configure

---

### Post by lovinglinux on 2010-04-27
> **Riffronan said:**
> Thanks for the suggestions...I even tried to make sure the right libraries were in place..Mozilla's development center says to :

apt-get build-dep firefox

apt-get install mercurial libasound2-dev libcurl4-openssl-dev libnotify-dev libxt-dev libiw-dev mesa-common-dev autoconf2.13

but everytime I do the  ./configure, I get a configure: error: --enable-application=APP was not specified and is required...as a last entry..so I'm still working on it

Do you really want to compile Firefox? If you are just looking for installing it, then [see this](http://lovinglinux.megabyet.net/?page_id=220##1---Manual-installation-of-fresh-final-releases-from-Mozilla-3). If you really want to compile it, ignore all previous suggestions and [see this](http://lovinglinux.megabyet.net/?page_id=220#Compiling-Firefox-1) (please I'm not criticizing, just pointing the right direction).

---

### Post by Riffronan on 2010-04-28
your comment, lovinglinux, took me to the mozilla page where I could run the latest stable version which is great but I was curious to play around with 3.7 alpha 4 so I think I may have figured something out.  The file I originally downloaded had "source" in its title and I'm no compiler by any means...so I 'Googled' my way to this page

  [http://www.mozilla.org/projects/devpreview/releasenotes/](http://www.mozilla.org/projects/devpreview/releasenotes/)

  I don't have a quick launch for it yet, but it'll run just fine with ./firefox

I appreciate very much all of your guys help!  

   Linux > Windows

---

### Post by pqwoerituytrueiwoq on 2010-04-28
for a 32 bit system just extract it to the desired location and launch the firefox script in it
for a 64 bit system it is a pain to get running and then you have plug in issues

---

### Post by lovinglinux on 2010-04-28
> **Riffronan said:**
> your comment, lovinglinux, took me to the mozilla page where I could run the latest stable version which is great but I was curious to play around with 3.7 alpha 4 so I think I may have figured something out.  The file I originally downloaded had "source" in its title and I'm no compiler by any means...so I 'Googled' my way to this page

  [http://www.mozilla.org/projects/devpreview/releasenotes/](http://www.mozilla.org/projects/devpreview/releasenotes/)

  I don't have a quick launch for it yet, but it'll run just fine with ./firefox

I appreciate very much all of your guys help!  

   Linux > Windows

You are welcome. If you want to test multiple versions of Firefox simultaneously without needing to extract them manualy, try my extension [FoxTester](http://lovinglinux.megabyet.net/?page_id=677). It is still a development version, but works for me.

---

### Post by bodhi.zazen on 2010-04-28
Personally I "install" firefox in /usr/local

```
sudo -i
rm -rf /usr/local/firefox
tar xvf firefox*.tar.gz -C /usr/local
```And I create a custom launcher / menu entry to run /usr/local/firefox/firefox .

You could just as easily create a launcher 

~/Downloads/firefox/firefox

See also :

[http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux](http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux)

FYI: You may download firefox as a binary or as source code, so advice on installing is somewhat dependent on how one wishes to install firefox.

You may also use one of the various ppa , but, in this case, I find download & extract just fine.

---

### Post by gadolinio on 2010-04-28
I don't mean to start a conflict, really. Just give my opinion.
 

 > **overlordchin said:**
>  Generally there is a configure file in there. If there is type "./configure" 

> **lovinglinux said:**
>  Anyway, when we are not sure about which file the user has, is better to ask first instead of giving compiling commands.
 
 

 @ lovinglinux
 overlordchin gave advice under a conditional. If the OP happens to have source code, he is receiving help on what to do with it. So overlordchin isn't just giving commands. And it is actually easier to say “if A, then do B”, than your suggested “is A true?” and then waiting for confirmation before saying “well, then do B”. If “A” isn't the case, it's already established that “B” isn't to be done.
 

 If we're talking about saying things without knowing the facts:
 

 > **lovinglinux said:**
> 
  The OP doesn't specify, but most likely he/she got the ready-to-run binaries and just want to launch Firefox.
 
 when
 > **Riffronan said:**
>  The file I originally downloaded had "source" in its title
 

 

 > **lovinglinux said:**
> 
 (…)  when we are not sure about which file the user has, is better to ask first (…) 
 :-o
 

 

 We're all trying to help here, and suggestions are not to be criticized. You can disagree with a post, but do not turn that into a specific critic to the user. The post you disagree with isn't harmful; it is just a piece of advice. What's wrong about that?
 

 Here's some interesting link:
 [https://launchpad.net/codeofconduct/1.1](https://launchpad.net/codeofconduct/1.1)

---

### Post by lovinglinux on 2010-04-29
> **gadolinio said:**
> overlordchin gave advice under a conditional. If the OP happens to have source code, he is receiving help on what to do with it. So overlordchin isn't just giving commands.

No, he is not. That's not the way Firefox is compiled. Additionally, IMO, users that are not familiar with all this stuff should be oriented to use "checkinstall" instead of "make install". 

See [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

> **gadolinio said:**
> And it is actually easier to say &#8220;if A, then do B&#8221;, than your suggested &#8220;is A true?&#8221; and then waiting for confirmation before saying &#8220;well, then do B&#8221;. If &#8220;A&#8221; isn't the case, it's already established that &#8220;B&#8221; isn't to be done.

You are preaching to the choir.

> **gadolinio said:**
>  If we're talking about saying things without knowing the facts:
  
Please don't distort my words. I never said I knew the facts and even acknowledged the possibility of being wrong assuming the user didn't want to compile Firefox. What I said was that if we don't have enough information, then we shouldn't jump to a conclusion based solely on the file format and provide instructions for the least probable and most complicated scenario. [Occam's razor](http://en.wikipedia.org/wiki/Occam%27s_razor) principle.

Besides, I did check when the OP registered in the forums and how many posts s/he has to make my judgment. Based on that information, was more likely that the user had just downloaded binaries and wanted to install it. Ironically, I was wrong about the first, but right about the second:

> **Riffronan said:**
> The file I originally downloaded had "source" in its title and I'm no compiler by any means...
 

> **gadolinio said:**
> We're all trying to help here, and suggestions are not to be criticized. You can disagree with a post, but do not turn that into a specific critic to the user.

I didn't mean to be rude with my first post and I still believe I wasn't. Perhaps the fact that my English is not so good is preventing me from seeing what you are seeing. Nevertheless, I was indeed correcting the information provided. What's wrong about that? That's also how we learn.

> **gadolinio said:**
> The post you disagree with isn't harmful; it is just a piece of advice. What's wrong about that?

I agree about not being harmful. Nevertheless, I have already spent hours trying to fix other user systems, because they followed wrong advice that started with the best of the intentions, just like here. I have already seen threads that starts with a innocent suggestion and turns into a mess, due to a series attempts to fix the problems caused by the first wrong suggestion. The most frustrating thing is that when that happens, the real solution is usually extremely simple and could be reached fast, if all the persons involved in discussion pays a little more attention to the original post instead of presuming the most complicated scenario and start  playing Dr. House.

> **gadolinio said:**
>  Here's some interesting link:
 [https://launchpad.net/codeofconduct/1.1](https://launchpad.net/codeofconduct/1.1)

Yes, [I know about that](https://launchpad.net/~lovinglinux). I never had a single infraction on these forums and I post here almost every day since August 21st, 2008.

I'm not saying I don't have bad days in which I behave like [Mr. Hyde](http://www.flamewarriors.com/warriorshtm/jekylhyde.htm). I do. But this discussion wasn't one of them.

---

### Post by gadolinio on 2010-04-29
“No, he is not. That's not the way Firefox is compiled.”
· I said that the OP is receiving help in case the conditional resulted true. The advice might be completely useless; but referring to the user's intention, he is at least willing to help. Of course, we could discuss if the verb help requires being actually helpful/succesful, and you're probably right there (although compiling was needed with that package, so the OP was given at least a right orientation). I'm talking about attitudes. One can ignore how FF specificly is compiled, and reply how to compile “standard” software, and one wouldn't know that the given command doesn't do the job. How could one refrain from answering, while ignoring the fact that one is actually wrong?
The easy/passive/less-energy-consuming system is: let user A answer how to deal with a certain condition, and let user B correct him if he's wrong. But don't tell user A that he shouldn't have given the answer in the first place. These forums work that way. The risk would be unintentionally harmful commands; fortunately, this is not the case. (and don't know the Forum's policy in that case).

"Additionally, IMO, users that are not familiar with all this stuff should be oriented to use "checkinstall" instead of "make install". "
· I completely agree with you. Haha I was in fact about to suggest that before... I should have. +1
  
“What I said was that if we don't have enough information, then we shouldn't jump to a conclusion based solely on the file format and provide instructions for the least probable and most complicated scenario.”
· If you assumed the slight chance of being wrong, based in probabilities, even more does a user that uses a conditional to say that generally there's a configure file, and says how to use it if it is the case. There was no jumping to a conclusion based solely in the package format. A conditional isn't a straight conclusion; a judgement based solely in chances/probabilities, is. And, my point is, such a critic wasn't therefore adequate.
  
“I didn't mean to be rude with my first post and I still believe I wasn't.”
· Having read you reply to me, I honestly believe you didn't mean to.

“Nevertheless, I was indeed correcting the information provided.”
· That's right. But maybe it would have been better to simply say something like “Be aware that firefox also packages binaries as .tar.bz2, and chances are you have those and not source code. Furthermore, firefox isn't compiled like that”. No critics to the user who offered another answer, that may even be completely useless, but whose attitude of contributing with knowlegde wasn't wrong.

“I agree about not being harmful. Nevertheless, I have already spent hours trying to fix other user systems, because they followed wrong advice that started with the best of the intentions, just like here. I have already seen threads that starts with a innocent suggestion and turns into a mess, due to a series attempts to fix the problems caused by the first wrong suggestion. The most frustrating thing is that when that happens, the real solution is usually extremely simple and could be reached fast, if all the persons involved in discussion pays a little more attention to the original post instead of presuming the most complicated scenario and start playing Dr. House. ”
· Yes, I know that happens. And of course I have no complaint about you warning the OP that what another user says isn't accurate; By doing that you help the OP.

“Yes, I know about that. I never had a single infraction on these forums and I post here almost every day since August 21st, 2008. ”
· You know, to be honest, right now I think there was no need for me to post that link. Well, maybe someone could find it interesting... haha. But shouldn't have directed it to you. Sorry about that.

---

### Post by Riffronan on 2010-05-02
good stuff, guys!  I have just downloaded 10.04 LTS, installed her aside Windows XP and run Google Chrome in Firefox's stead...10.04 is my new baby...Windows is only for running Amplitube3 and Adobe Audition for audio file manipulation...Thank you again for your help (!)

  Linux > Windows

---

### Post by tommark on 2010-05-02
I,too, am noobish. I've installed "build-essential" and "libgtk2.0-dev"; have un-tarred the program I want to install (muCommander), and have moved into its folder.
But now when I type "./configure", the terminal tells me "no such file or directory"
What do I need to do to configure my muCommander?
Thank you

---

### Post by oldos2er on 2010-05-02
Much easier to install the *deb file: [http://www.mucommander.com/download/mucommander_0.8.5_all.deb](http://www.mucommander.com/download/mucommander_0.8.5_all.deb)

---

