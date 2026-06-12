---
title: "Grr. Firefox issues. Pulling Hair Out"
date: 2012-02-22
forum: General Help
---

### Post by rhugga on 2012-02-22
I'm running 10.04 LS 32-bit.

Occasionally I get this problem with Firefox (version 9.x - 10.x) where I get the following error dialog when launching firefox:

"Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features."

The only way I have found to fix this is to delete my $HOME/.mozilla diretory and start fresh.. which is a pain to re-setup all my mods and tweaks..

This happens on 3 different ubuntu 10.4 installation of mine. My workstation at work, my workstation at home, and in a vmware session on my macbook. All running 32-bit and current with all updates.

Very frustrating. Firefox is not the robust, non-bloated browser that lured me to it in the first place.

---

### Post by winh8r on 2012-02-22
I cannot offer an instant solution here, but you can have multiple firefox profiles which you can choose from , have a look here and try setting up a basic profile for accessing the work related stuff, and have another personal profile which can be more customised and might resolve the issue with the warnings.

I was thinking that maybe it is because you need to use a "client" like novell or citrix to access your work environment , that there is some additional security feature for your work related stuff that is putting an extra layer of security into your profile , but Firefox has no control over it (for security reasons!) and this is causing the warnings.

Anyway, take a look here on how to set up profiles:
[http://chrisjean.com/2009/02/23/multiple-firefox-profiles-in-ubuntu/]("http://chrisjean.com/2009/02/23/multiple-firefox-profiles-in-ubuntu/")

Or perhaps someone more well versed in the inner workings of Firefox will be able to give you a definitive answer.

Hope this is of some little help to you.

---

### Post by lovinglinux on 2012-02-22
That happened to me when I moved my files to a new computer this month. The problem is that when I copied the files, file permissions were changed for some reason.

I don't know exactly which file is causing the alert, but I can offer a solution.

Create a new profile using the profile manager.

```
firefox -P
```

Close Firefox, start it again using the new profile. Close it again. This will create the basic file structure under the new profile folder.

Open the new profile folder and your default profile side-by-side, with the file manager. Check the permissions of each file in the new profile and replicate the permissions in the default profile.

If you don't want to do that, you can copy the important stuff from the old profile to the new one and delete the old one.

Check this article for some important files: [http://www.webgapps.org/tutorials/firefox/troubleshooting/fixing-corrupted-profiles](http://www.webgapps.org/tutorials/firefox/troubleshooting/fixing-corrupted-profiles)

---

