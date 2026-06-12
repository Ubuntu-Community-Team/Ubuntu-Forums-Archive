---
title: "Ubuntu Software Centre won't open"
date: 2011-11-25
forum: General Help
---

### Post by torontopronto on 2011-11-25
Hi I'm relatively new to the Ubuntu Forum.  I followed the post of that  was given here to get my webcam to work on skype.  Yep I was impressed,  my webcam works on skype and all is well.

BUT !!! Now I cannot open the Ubuntu Software Centre.

I ran a the command: sudo apt-get update
and my terminal responded with:

E: Malformed line 61 in source list /etc/apt/sources.list (dist parse)
E: The list of source could not be read.

Can someone please help...!!!:sad:

---

### Post by MG&amp;TL on 2011-11-25
Can you open your terminal again and copy and paste the output of the following command, wrapping it in Code tags (the hash button) please?

```
cat /etc/apt/sources.list
```

A link to the instructions you followed would be helpful.

---

### Post by drs305 on 2011-11-25
You have an incorrect line in the file which contains your repository list.

Open /etc/apt/sources.list as root. The following command will open Gedit on the line with the error:
```
gksu gedit +61 /etc/apt/sources.list
```

The entries in this file generally take the format as the example below. Some of the information, such as the server and release, may be different on your system:
> deb [http://www.gtlib.gatech.edu/pub/ubuntu/](http://www.gtlib.gatech.edu/pub/ubuntu/) oneiric main restricted universe multiverse

If you don't understand the error, either place a # symbol in front of the entire line (which disables it) and save the file, or post the contents of the entire file here so we can review it.

If you fix the error, run:
```
sudo apt-get update
```

Here is a link to an explanation of the Repositories:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by torontopronto on 2011-11-28
For starters, I want to say, thank you very much for responding, I do appreciate your effort in helping me.

Okay let me show you what I have come up with one step at a time:

In response to **drs305** and **MG&TL** - I noted that if I type either of your codes I get the same response

And here is the response that I got: (again your help will be appreciated)

  	 	 	 	p { margin-bottom: 0.21cm; }  # deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted 
 # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
 # newer versions of the distribution. 
  
 deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick main restricted 
 deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick main restricted 
  
 ## Major bug fix updates produced after the final release of the 
 ## distribution. 
 deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates main restricted 
 deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates main restricted 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
 ## team. Also, please note that software in universe WILL NOT receive any 
 ## review or updates from the Ubuntu security team. 
 deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick universe 
 deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick universe 
 deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates universe 
 deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates universe 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
 ## team, and may not be under a free licence. Please satisfy yourself as to  
 ## your rights to use the software. Also, please note that software in  
 ## multiverse WILL NOT receive any review or updates from the Ubuntu 
 ## security team. 
 deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick multiverse 
 deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick multiverse 
 deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates multiverse 
 deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates multiverse 
  
 ## Uncomment the following two lines to add software from the 'backports' 
 ## repository. 
 ## N.B. software from this repository may not have been tested as 
 ## extensively as that contained in the main release, although it includes 
 ## newer versions of some applications which may provide useful features. 
 ## Also, please note that software in backports WILL NOT receive any review 
 ## or updates from the Ubuntu security team. 
 # deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse 
 # deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse


  
 ## Uncomment the following two lines to add software from Canonical's 
 ## 'partner' repository. 
 ## This software is not part of Ubuntu, but is offered by Canonical and the 
 ## respective vendors as a service to Ubuntu users. 
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner 
 # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner 



  
 ## This software is not part of Ubuntu, but is offered by third-party 
 ## developers who want to ship their latest software. 
 deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main 
 deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main 



  
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse 



  
 # libv4l PPA 
 deb [http://ppa.launchpad.net/libv4l/ppa/ubuntu](http://ppa.launchpad.net/libv4l/ppa/ubuntu)  main

---

### Post by drs305 on 2011-11-28
> **torontopronto said:**
> 
  	 	 	 	**[COLOR="DarkRed"]p { margin-bottom: 0.21cm; } [/COLOR]** # deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted 
 # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
 # newer versions of the distribution. 
  


This is at least one of the problems (if it isn't the only one). Remove the items in **[COLOR="DarkRed"]bold dark red[/COLOR]** so that line looks like:
> 
 # deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted 


You can open the editor as root with:
```
gksu gedit /etc/apt/sources.list
```
Make the change, save the file, but leave it open. Then:
```
sudo apt-get update
```
to see if there are any further errors.

If it gives an error, it will tell you the line number (or last line). Inspect that line in your open file. You can enable line numbers via Edit, Preferences.

---

### Post by torontopronto on 2011-11-28
Thanks for the response.

I think the words "**[COLOR=DarkRed]p { margin-bottom: 0.21cm; } [/COLOR]**" actually come from me pasting the response from my terminal onto the word processor and then back onto this site.  If I type in the code:

gksu gedit /etc/apt/sources.list

and then paste the response from the new window (as shown below) the statement in red is not there.  Now if I follow your advice to show the line numbers (edit - preferences) I see that line 61 is the very last line of the statement pasted below.  That line reads:

deb [http://ppa.launchpad.net/libv4l/ppa/ubuntu](http://ppa.launchpad.net/libv4l/ppa/ubuntu)  main

What do you think is wrong with the line above?  Could it be a spacing?  I noticed that there are two spaces open between the last word "ubuntu" and the word "main"

Thanks in advance.



# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse

# libv4l PPA
deb [http://ppa.launchpad.net/libv4l/ppa/ubuntu](http://ppa.launchpad.net/libv4l/ppa/ubuntu)  main

---

### Post by torontopronto on 2011-11-28
just as a follow up to my last post.  I made the modification myself (removed one of the spaces) then save the file (leaving it open).  Then I ran the command line:
sudo apt-get update
But I still get the same error:

E: Malformed line 61 in source list /etc/apt/sources.list (dist parse)
E: The list of source could not be read.

So I have gone back to the file and put back the space (it is obviously not the problem).

I wonder what is wrong with the line:

deb [http://ppa.launchpad.net/libv4l/ppa/ubuntu](http://ppa.launchpad.net/libv4l/ppa/ubuntu)  main

---

### Post by torontopronto on 2011-11-28
I APPEAR TO HAVE SOLVED THE PROBLEM !!!

I simply removed line 61 altogether and ..... hey presto everything appears to be working.  I have the Ubuntu Software Centre back and my Webcam is working on Skype.

**drs305** - Do want to thank you for taking some time to even bother trying to solve my issue.

**again thanks !!!**

---

### Post by drs305 on 2011-11-28
Glad you figured it out. I was called out on a business trip as you were solving things on your own.

Please mark the thread SOLVED via the 'Thread Tools' link near the top right of the first post.

Happy Ubuntu-ing !

---

