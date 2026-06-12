---
title: "Google Gears in Firefox 3.5.1"
date: 2009-07-23
forum: General Help
---

### Post by dwally89 on 2009-07-23
Hi,

According to this article [http://www.techno360.in/now-google-gears-supports-firefox-3-5-1/](http://www.techno360.in/now-google-gears-supports-firefox-3-5-1/) Google Gears is now supported in Firefox 3.5.1, but when I go to [http://gears.google.com/](http://gears.google.com/) and install it, it comes up with the error message of "Google Gears 0.5.29.0 could not be installed because it is not compatible with Firefox 3.5.1."

Google Gears 0.5.30.0 should be the version it is installing, not version 0.5.29.0

Has anyone else had this problem?

---

### Post by falsehope on 2009-07-23
Yes,
Same issue here.  :confused:

---

### Post by andresmh on 2009-07-23
Same here. How did you install FF 3.5.1? I did it via Synaptic and instead of replacing the older Firefox it added a new browser (Shiretoko) to my Internet menu. Internally it's called firefox-3.5.

When I go to [http://gears.google.com](http://gears.google.com) I get "Your browser is not currently supported. Please check the list of supported browsers below." But then if I go to [http://gears.google.com/download.html](http://gears.google.com/download.html) it download [http://dl.google.com/gears/current/gears-linux-opt.xpi](http://dl.google.com/gears/current/gears-linux-opt.xpi) but then when installing it, it throws the same error you mention.

I wonder if it's just a matter of repackaging the XPI file to match the same user agent info. What user agent info do you get?

Mine is:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.1) Gecko/20090716 Ubuntu/9.10 (karmic) Shiretoko/3.5.1

You can get yours at [http://whatsmyuseragent.com/](http://whatsmyuseragent.com/)

---

### Post by andresmh on 2009-07-23
aha! I got this XPI and it worked:
[http://ubuntuforums.org/showthread.php?p=7622069](http://ubuntuforums.org/showthread.php?p=7622069)

---

### Post by dwally89 on 2009-07-23
> **andresmh said:**
> Same here. How did you install FF 3.5.1? I did it via Synaptic and instead of replacing the older Firefox it added a new browser (Shiretoko) to my Internet menu. Internally it's called firefox-3.5.

When I go to [http://gears.google.com](http://gears.google.com) I get "Your browser is not currently supported. Please check the list of supported browsers below." But then if I go to [http://gears.google.com/download.html](http://gears.google.com/download.html) it download [http://dl.google.com/gears/current/gears-linux-opt.xpi](http://dl.google.com/gears/current/gears-linux-opt.xpi) but then when installing it, it throws the same error you mention.

I wonder if it's just a matter of repackaging the XPI file to match the same user agent info. What user agent info do you get?

Mine is:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.1) Gecko/20090716 Ubuntu/9.10 (karmic) Shiretoko/3.5.1

You can get yours at [http://whatsmyuseragent.com/](http://whatsmyuseragent.com/)

I installed Firefox just by downloading it off the website.

---

### Post by dwally89 on 2009-07-23
> **andresmh said:**
> aha! I got this XPI and it worked:
[http://ubuntuforums.org/showthread.php?p=7622069](http://ubuntuforums.org/showthread.php?p=7622069)

Yep works for me too :-)

---

### Post by sandeepjshenoy on 2009-07-23
@[andresmh]("http://ubuntuforums.org/member.php?u=636245") you can get the latest version of firefox ie 3.5.1 using ubuntuzilla [http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/) it automatically updates to a new version when released.

---

### Post by dwally89 on 2009-07-24
> **sandeepjshenoy said:**
> @[andresmh]("http://ubuntuforums.org/member.php?u=636245") you can get the latest version of firefox ie 3.5.1 using ubuntuzilla [http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/) it automatically updates to a new version when released.

I just tried to install Ubuntuzilla, and I got the following error:

```
user@daniel-laptop:~$ ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.6.2

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://ubuntuzilla.sourceforge.net/ 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.5.1. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.org/)
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
Please choose the localization (language) for Firefox. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at http://ubuntuzilla.sourceforge.net/ for steps you can take to resolve this problem.]
  0. af           1. ar           2. as           3. be        
  4. bg           5. bn-BD        6. bn-IN        7. ca        
  8. cs           9. cy          10. da          11. de        
 12. el          13. en-GB       14. en-US       15. eo        
 16. es-AR       17. es-CL       18. es-ES       19. es-MX     
 20. et          21. eu          22. fa          23. fi        
 24. fr          25. fy-NL       26. ga-IE       27. gl        
 28. gu-IN       29. he          30. hi-IN       31. hr        
 32. hu          33. id          34. is          35. it        
 36. ja          37. ka          38. kk          39. kn        
 40. ko          41. ku          42. lt          43. lv        
 44. mk          45. ml          46. mn          47. mr        
 48. nb-NO       49. nl          50. nn-NO       51. oc        
 52. or          53. pa-IN       54. pl          55. pt-BR     
 56. pt-PT       57. rm          58. ro          59. ru        
 60. si          61. sk          62. sl          63. sq        
 64. sr          65. sv-SE       66. ta-LK       67. ta        
 68. te          69. th          70. tr          71. uk        
 72. vi          73. zh-CN       74. zh-TW     
Enter your choice of localization (integer, from 0 to 74): 13
You have chosen localization en-GB. Is that correct [y/n]? 
Please enter 'y' or 'n': y

Updating repositories information with apt-get update. You may be prompted for your password.

Hit http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-en_GB
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_GB
Hit http://il.archive.ubuntu.com jaunty Release.gpg                  
Get: 1 http://il.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]
Hit http://archive.canonical.com jaunty Release.gpg                            
Ign http://archive.canonical.com jaunty/partner Translation-en_GB              
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_GB      
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com jaunty-security Release                         
Hit http://archive.canonical.com jaunty Release                                
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Hit http://archive.canonical.com jaunty/partner Packages       
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources                    
Hit http://security.ubuntu.com jaunty-security/restricted Sources              
Hit http://archive.canonical.com jaunty/partner Sources                        
Hit http://security.ubuntu.com jaunty-security/universe Packages               
Hit http://security.ubuntu.com jaunty-security/universe Sources 
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Get: 2 http://il.archive.ubuntu.com jaunty/restricted Translation-en_GB [4640B]
Get: 3 http://il.archive.ubuntu.com jaunty/universe Translation-en_GB [35.2kB]
Get: 4 http://il.archive.ubuntu.com jaunty/multiverse Translation-en_GB [47.5kB]
Hit http://il.archive.ubuntu.com jaunty-updates Release.gpg          
Ign http://il.archive.ubuntu.com jaunty-updates/main Translation-en_GB
Ign http://il.archive.ubuntu.com jaunty-updates/restricted Translation-en_GB
Ign http://il.archive.ubuntu.com jaunty-updates/universe Translation-en_GB
Ign http://il.archive.ubuntu.com jaunty-updates/multiverse Translation-en_GB
Hit http://il.archive.ubuntu.com jaunty Release
Hit http://il.archive.ubuntu.com jaunty-updates Release                     
Hit http://il.archive.ubuntu.com jaunty/main Packages
Hit http://il.archive.ubuntu.com jaunty/restricted Packages
Hit http://il.archive.ubuntu.com jaunty/main Sources
Hit http://il.archive.ubuntu.com jaunty/restricted Sources
Hit http://il.archive.ubuntu.com jaunty/universe Packages
Hit http://il.archive.ubuntu.com jaunty/universe Sources
Hit http://il.archive.ubuntu.com jaunty/multiverse Packages
Hit http://il.archive.ubuntu.com jaunty/multiverse Sources
Hit http://il.archive.ubuntu.com jaunty-updates/main Packages
Hit http://il.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://il.archive.ubuntu.com jaunty-updates/main Sources
Hit http://il.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://il.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://il.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://il.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://il.archive.ubuntu.com jaunty-updates/multiverse Sources
Fetched 140kB in 1s (116kB/s)
Reading package lists... Done

Making sure that the repositories version of Firefox is installed...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Backing up old Firefox preferences

Retrieving package name for Firefox ...
Success!: firefox-3.5.1.tar.bz2

Downloading Firefox archive from the Mozilla site

--2009-07-24 10:43:54--  ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-GB/firefox-3.5.1.tar.bz2
           => `firefox-3.5.1.tar.bz2'
Resolving releases.mozilla.org... 131.188.12.212, 216.165.129.141, 204.152.184.196, ...
Connecting to releases.mozilla.org|131.188.12.212|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-GB ... done.
==> SIZE firefox-3.5.1.tar.bz2 ... 9650907
==> PASV ... done.    ==> REST 10036025 ... done.    
==> RETR firefox-3.5.1.tar.bz2 ... 
No such file `firefox-3.5.1.tar.bz2'.

wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-GB/firefox-3.5.1.tar.bz2
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1151, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 211, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 238, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 604, in install
    self.downloadPackage()
  File "/usr/local/bin/ubuntuzilla.py", line 773, in downloadPackage
    self.util.robustDownload(argsdict={'executionstring':"wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://" + "%mirror%" + self.options.package + "/releases/" + self.releaseVersion + "/linux-i686/"+ self.locList[self.locChoice] + "/" + self.packageFilename, 'includewithtest':True})
  File "/usr/local/bin/ubuntuzilla.py", line 155, in robustDownload
    self.execSystemCommand(**argsdict)
  File "/usr/local/bin/ubuntuzilla.py", line 141, in execSystemCommand
    print >>sys.stderr, result
NameError: global name 'result' is not defined

```

---

### Post by nanotube on 2009-07-24
hi
yea that was due to a silly error on my part
try the dev version of 4.6.3, as attached to this bug report:
[https://sourceforge.net/tracker/?func=detail&aid=2825626&group_id=202789&atid=982990](https://sourceforge.net/tracker/?func=detail&aid=2825626&group_id=202789&atid=982990)

update: this has now been released, so just grab the latest directly from the ubuntuzilla website.

---

### Post by Ingenium on 2009-07-24
Google gears installed fine for me just now, but it broke my gmail accounts. The normal gmail account works, but it gets an error shortly after it starts syncing saying I need to reload gmail. It completely breaks my Google Apps for Domains gmail account -- the loading progress bar gets halfway across then it just stops. It also gives "internal error" when I try to turn on Offline mode for my calendar. 

Guess it's time to disable Gears and hope it's fixed soon.

---

### Post by geistteufel on 2009-07-27
Hi !
This is my first post.

For anyone who want a french (and maintain) version of lastest Google Gears (working nice on firefox 3.5.1), please look at there :

[http://blog.celogeek.com/linux-en/linux-tips-and-tricks/google-gears-compilation-en/](http://blog.celogeek.com/linux-en/linux-tips-and-tricks/google-gears-compilation-en/)

I explain how to make it, and often add a XPI version from lastest revision (take it from SVN on trunk).

Actually I got 0.5.32 version for both 32 bits and 64 bits firefox.

So as soon as new version come, I will post a new revision (so subscribe to the post to be sure to get update as soon as I made it :))

Celogeek !

---

### Post by dcunited on 2009-07-28
I was able to get it installed on the Shiretoko install on 32-bit by going to the [download link]("http://dl.google.com/gears/current/gears-linux-opt.xpi").

---

### Post by ddreggors on 2009-07-28
> **andresmh said:**
> 
Mine is:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.1) Gecko/20090716 Ubuntu/9.10 (karmic) Shiretoko/3.5.1

You can get yours at [http://whatsmyuseragent.com/](http://whatsmyuseragent.com/)



Or a more simple approach... Select the 'Help' menu and click 'About Shiretoko'.

Gives the same string. This works for any version of FF I believe.

;-)

---

