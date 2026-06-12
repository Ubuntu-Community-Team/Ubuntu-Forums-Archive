---
title: "Nothing is trusted"
date: 2012-02-04
forum: General Help
---

### Post by DENNISLINUXX64 on 2012-02-04
I HAD INSTALLED AND USED UBUNTU 11.10 X64 FOR ABOUT 4 DAYS.

ALL OF SUDDEN IT WILL NOT UPDATE. IT SAYS NOT TRUSTED SOURCE, OR FROM NOT TRUSTED SOURCE.

WELL ON THE 32 BIT VERSION IN THE PAST I WOULD HAVE EDITED THE SOURCE TO FIX THIS...BUT NONE OF THAT APPEARS TO BE AVAILABLE ON X64.

IT WILL NOT ALLOW VLC TO PLAY VIDEOS TO INSTALL SAME MESSAGE. AND BLOCS INTERNET ACCESS TO DOWNLOAD INSTALL PACKAGE. SAY INTERNET NOT WORKING.

I DOWNLOADED CHROME AND TRIED TO INSTALL IT AND IT BLOCKS THE INSTALL AND CLOSES THE INTERNET CONECTION TO NOT ALLOW IT DOWNLOAD THE PACKGES.

SO WHAT HAPPENED BETWEEN THE THE NICE INSTALL AND NOW....THAT NOTHING WILL WORK....

CURIOUS MINDS WANT TO KNOW....

THANKS
DENNIS:confused:

---

### Post by durand on 2012-02-04
This is because you must have installed a repository that isn't signed or you don't have a key for it. It's pretty easy to fix in most cases. Open the launcher, search for "Terminal" and open that. Then type:
```
sudo apt-get update
``` and post the output. It will tell us which repos you installed are missing keys.

---

### Post by coffeecat on 2012-02-04
@DENNISLINUXX64, please do not post in all caps. From the forum [Code of Conduct](http://ubuntuforums.org/index.php?page=policy):

> ALL CAPS is interpreted as screaming.

Or is your caps lock on? :wink:

---

### Post by DENNISLINUXX64 on 2012-02-04
here is the out put..i am going blind so small letters are not easy to read. i am sorry that the forum is not friendly to people that have vision problems. i will point this out to my vision impaired friends that visually impaired folks are not wanted. please help people instead of causing them not to get the information needed.

```

Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                                                                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                                                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                                                         
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                                         
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                                                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease                               
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main amd64 Packages             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner amd64 Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main amd64 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted amd64 Packages                  
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe amd64 Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse amd64 Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en             
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Translation-en

```

i am very concerned that these were changed with ubuntu not asking permission to change repository and not trust anything.
it took the first 239 updates without questions the day it installed. is this common for x64 to change repositorys and access on its own?

thank you for your time.

i will remember that visually affected people must suffer and type all small letters.

dennis:confused:

---

### Post by drs305 on 2012-02-04
I've edited your post to include the output in 'code' tags. This takes up less space and generally allows for easier viewing by forum users.

You generate the code tags when creating a post by highlighting the text and then clicking the # icon in the post's menu. This places the content between [noparse] ```
 
``` [/noparse] tags or you can type the codes manually. 

If you would like to quote something, use "QUOTE" tags, or press the yellow icon in the menu.

We try to keep the look of all the Ubuntu forums standardized for a better viewing experience. We welcome all viewers, and Ubuntu has many features explicity added to assist those with special needs. They are normally found in the Accessibility or 'Universal Access' sections of the OS.

As far as the use of CAPS, most browsers will allow the user to increase the font size on the users machine. This should be a good tradeoff between users who are visually impaired and the majority of users who can see the normally-sized fonts on the Ubuntu forums.

---

As for your problem, try opening a terminal and typing:
```
sudo apt-get update
sudo apt-get upgrade
```
It may ask if you want to allow the sources to me marked as trusted. Typing 'Yes' or 'Y' and pressing enter may resolve your issue.

---

### Post by DENNISLINUXX64 on 2012-02-04
nope no help so far.

but many lectures on procedure and no solutions.

hope fully some one will help me with my problem which is that nothing is trusted.

it still comes up after the suggestion.

no way to added trust as in y or yes was made available on the upgrade command.

rather than lectures on procedure, protocol ect could i please get a suggestion that will provide some help.

sorry to have to keep asking the same question but i have not received a answer to question merely a series of lectures on protocol. 

i am really sorry that protocol is more important than information.

hopefully this time since i am following all the protocols. i may get a answer. no caps, and no long information.

dennis:confused:

---

### Post by scarleo on 2012-02-04
You have probably added a PPA and didn't have the keys imported correctly. Either fix that, there's info in the PPA on how to import keys, or go to Synaptic (install it if it's not installed) and click on "Mark all upgrades" then Apply. Synaptic will also complain about the sources not being trusted but will let you continue the upgrade.

---

### Post by emiller12345 on 2012-02-04
This should tell you which repos you have enabled on your machine
```
~$ find /etc/apt/ -type f -path '/etc/apt/sources.list*' -a -not  -path '/etc/apt/sources.list*.save' -exec grep -v -e "^#" -e "^$" '{}'  \; | sort
```I believe the default sources are something like 
[http://security.ubuntu.com](http://security.ubuntu.com)
[http://*.archive.ubuntu.com](http://*.archive.ubuntu.com)

EDIT:
In Firefox if you do [Ctrl] and + it will increase the font size making it easier to see.
[Crtl] and 0 will reset the font size (Zero)

---

### Post by durand on 2012-02-04
Hmm, weird. Normally if a repo is missing a key, it says that when you run that command but there's nothing coming up here. What happens when you run ```
sudo apt-get upgrade
``` as suggested by drs305? You need to post the output/errors here. Or take a screenshot of the error message you get when you're trying to install something. You can take a screenshot by pressing the PrntScrn button on your keyboard.

---

### Post by DENNISLINUXX64 on 2012-02-04
hi here is the output you wanted.

> dennis-linux-x64@dennislinuxx64-HP-Compaq-dc5750-Small-Form-Factor:~$ sudo apt-get upgrade
[sudo] password for dennis-linux-x64: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgrade

this has changed since i ran the first two times.

so is this what i am supposed to see.....

thank you for your help this is the first change i have seen.

dennis:o

---

### Post by DENNISLINUXX64 on 2012-02-04
but why is Ubuntu importing software with invalid keys.....this is a serious change to the os, with repercussions....it would seem that this needs to be fixed.

just a thought from some one that had it happen and still doesn't know what fixed it...so to speak or at least changed it.

got chrome to install...

still no vlc....

still no update....on update will lock up and freeze machine.twice.

so while better their still is a change that occurred logic should dictate that this not be allowed to happen.

the add the other software to up date did not allow it update either....it froze up and locked their also.

thanks 
dennis:confused::confused:

---

### Post by durand on 2012-02-04
I'm pretty sure nothing has been changed by them. I haven't seen any differences so its probably just something at your end. What error do you get when you try to install vlc? It really should just work.

Also, FYI, x86_64 is practically the same as i386, the only differences are that everything is compiled to utilise your hardware more completely and there is an extra compatibility layer so that you can still run i386 software. It shouldn't change your software in any other way.

---

### Post by uRock on 2012-02-04
To change the size of fonts, as you see them in your browser, hit Ctrl+ or Ctrl-.

---

### Post by DENNISLINUXX64 on 2012-02-04
i see its deteriorated to the user is at fault...i would have thought the Linux folks would understand that sometimes a small change can cause big changes.

having worked in the it business for 10 years...a+/n+/security+/ccna/ccnp/ccie in one more test. i have always been reluctant to blame the user. i usually find that someone changed something an unfortunately that they did not understand what the change might do. i am guessing that is what happened here.

fortunately i found out that it was a change. some one dropped me a note on a another group.

they provided a little patch that fixed it. appears that someone changed the way keys are used and didn't understand that could cause a issue. so now all keys are accepted and every thing works again...smile...guess it was my computer, my install ect...always the customer wrong.

have a good one and hopefully you will not have a user induced problem like this and no one be willing to do anything but tell you its your equipment and installs problem.

to those that tried thanks for the help. to those that caused problems and tried to convince me it was my fault. i can not convince my self to wish this on you as you would still not understand and learn.

good luck.

---

### Post by drs305 on 2012-02-04
> **DENNISLINUXX64 said:**
> 
to those that tried thanks for the help. 

Glad you were able to fix your problem.

You can help others with the same problem by posting the commands that corrected the problem and then marking this thread SOLVED via the 'Thread Tools' link near the top right of the first post.

---

