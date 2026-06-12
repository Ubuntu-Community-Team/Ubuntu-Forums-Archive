---
title: "The action would require the installation of packages from not authenticated sources?"
date: 2010-11-20
forum: General Help
---

### Post by binarylife on 2010-11-20
Hi
Since I while when I try to install something form Ubuntu software center or Update manager,It gives me this error msg :
The action would require the installation of packages from not authenticated sources.
Requires installation of untrusted packages

............................
Why is is untrusted ?
How Can I fix it ?

---

### Post by binarylife on 2010-11-20
p.S The Server is the main one .
Also there is a GPG error 

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by binarylife on 2010-11-21
Any help ?

---

### Post by czgMax on 2010-11-25
Hey,

If you just need help (because the thread is solved), I got the same problem and this worked for me:

First I read this post [http://ubuntuforums.org/showpost.php?p=8878470&postcount=3](http://ubuntuforums.org/showpost.php?p=8878470&postcount=3) after I googled it. It was not the solution to the problem but it worked very similar. I opened:

*System->Administration->Synaptic Package Manager*

Then:
[I]
Settings->Repositories[/I]

and first looked whether the checkbox "*Software restricted by copyright or legal issues*" was checked (in my case it was)

After this I went to the tab "*Other Software*" and checked "*Canonical Partners*" (if you have Source Code installed you may check "*Canonical Partners(Source Code)*" too) to allow Ubuntu to download from this sources.

Result: All updates should work as before.:p

Max

---

### Post by binarylife on 2010-11-26
> **czgMax said:**
> Hey,

If you just need help (because the thread is solved), I got the same problem and this worked for me:

First I read this post [http://ubuntuforums.org/showpost.php?p=8878470&postcount=3](http://ubuntuforums.org/showpost.php?p=8878470&postcount=3) after I googled it. It was not the solution to the problem but it worked very similar. I opened:

*System->Administration->Synaptic Package Manager*

Then:
[I]
Settings->Repositories[/I]

and first looked whether the checkbox "*Software restricted by copyright or legal issues*" was checked (in my case it was)

After this I went to the tab "*Other Software*" and checked "*Canonical Partners*" (if you have Source Code installed you may check "*Canonical Partners(Source Code)*" too) to allow Ubuntu to download from this sources.

Result: All updates should work as before.:p

Max


Yeah , I did almost the same . And it works fine with no problems .Anyway thank you Sam . : )

---

### Post by Terry19 on 2011-01-07
I have the same problem, but doing what was posted above did not solve it.

---

### Post by OzzyFrank on 2011-01-25
Didn't work for me either, as all those options were already checked. In my case, I had re-enabled a repo for Opera web browser that was of course disabled during the upgrade to Maverick, and it is this that is halting my upgrade process. Besides the fact I find it odd that [http://deb.opera.com/opera/](http://deb.opera.com/opera/) is looked at as an untrusted source, I thought there would have been a way to just ignore that and continue regardless, but this isn't the case. It just goes back to the Update Manager's main display, and I can find nothing useful in Software Sources... except that I can disable that repo there, which is something I want to avoid (especially since there is a new version of Opera for download). Any other solutions?

---

### Post by gresavage on 2011-01-26
> **ozzyfrank said:**
> didn't work for me either, as all those options were already checked. In my case, i had re-enabled a repo for opera web browser that was of course disabled during the upgrade to maverick, and it is this that is halting my upgrade process. Besides the fact i find it odd that [http://deb.opera.com/opera/](http://deb.opera.com/opera/) is looked at as an untrusted source, i thought there would have been a way to just ignore that and continue regardless, but this isn't the case. It just goes back to the update manager's main display, and i can find nothing useful in software sources... Except that i can disable that repo there, which is something i want to avoid (especially since there is a new version of opera for download). Any other solutions?

bump

---

### Post by DrFolger on 2011-01-26
in response to the key with opera, last week they released a new version which the whole purpose was just to install a new key. the old key was set to expire this month (jan 2011)

[http://my.opera.com/desktopteam/blog/2011/01/21/a-second-opera-11-00-final-build-for-linux-freebsd](http://my.opera.com/desktopteam/blog/2011/01/21/a-second-opera-11-00-final-build-for-linux-freebsd)

 if you can't upgrade via the update manager. just download opera from opera's website and re-install with the new package.

---

### Post by gresavage on 2011-01-26
> **DrFolger said:**
> in response to the key with opera, last week they released a new version which the whole purpose was just to install a new key. the old key was set to expire this month (jan 2011)

[http://my.opera.com/desktopteam/blog/2011/01/21/a-second-opera-11-00-final-build-for-linux-freebsd](http://my.opera.com/desktopteam/blog/2011/01/21/a-second-opera-11-00-final-build-for-linux-freebsd)

 if you can't upgrade via the update manager. just download opera from opera's website and re-install with the new package.

actually i solved this myself... another option would be to create a text file and name it A2019EA84E7532C8.gpg make sure to make the suffix .gpg and then go to: [http://deb.opera.com/](http://deb.opera.com/) and copy the key from the bottom of the page where it says: BEGIN PGP PUBLIC KEY BLOCK to where it says END PGP PUBLIC KEY BLOCK

then just add it to the authentication sources by  importing it using the "Import Key File..." button under System-> Administration-> Software Sources and navigate to the Authentication tab.

just navigate to the folder you saved the .gpg in and select it... and voisla! you may have to delete the old key from the repository i'm not sure. 

also you can delete the .gpg file as it is no longer necessary

or in terminal execute the following command:


```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```

i believe any of these suggestions would work

---

### Post by OzzyFrank on 2011-01-26
Hehe... I figured out myself it was to do with Opera's authentication key being out of date, and found the info on Opera's site, though for me the command-line solution (which is by far the easiest) didn't work - it just sat there after downloading it, doing nothing. So I copied the text of the key itself, and used that.

For those in a similar situation, ie the command doesn't work for you, it's easy enough to do it manually (by importing, as has been outlined already, and _pasting_, which is by far the easiest of the 2):

In the **Authentication** tab in **Software Sources**, you will note the ***Import Key File...*** button, which you can use to install a key you may have downloaded. If the key was displayed on the page itself - it's hard to miss, being a large block of text - copy it, along with the header and footer information. Then right-click the offending entry and choose **Add key from paste data**. You should then see a new entry for that program, so go back and select the out of date key and click the ***Remove*** button.

You should now be able to update your system, and fetch the latest version of Opera, of whatever program that was causing this.

I think the error message should say something more like "Updating cannot continue as the following program has an expired authentication key"... might need to go to Ubuntu Brainstorm with that!

---

### Post by SESteve on 2011-03-14
> **czgMax said:**
> After this I went to the tab "*Other Software*" and checked "*Canonical Partners*" (if you have Source Code installed you may check "*Canonical Partners(Source Code)*" too) to allow Ubuntu to download from this sources.

That's what did the trick for me.

---

### Post by lemaza on 2011-07-29
Hello 

I have ubuntu 11.04 ... i have the same problem when I use the update manager and the solution given didn't fix the problem , can somebody help ?

---

### Post by paniwani on 2011-09-16
> **sesteve said:**
> that's what did the trick for me.
+1

---

### Post by ranjit. on 2011-10-24
i found that useful, but just in case that doesnt work you  can install it via terminal, i got a similar issue when i tried to install grub-customizer, i just typed sudo apt-get upgrade grub-customizer and they it asked weather to verify the source, i just gave no and it got installed. I guess you can take that method if nothing else seems to work.

---

### Post by oldtimer7777 on 2011-10-24
> **ranjit. said:**
> i found that useful, but just in case that doesnt work you  can install it via terminal, i got a similar issue when i tried to install grub-customizer, i just typed sudo apt-get upgrade grub-customizer and they it asked weather to verify the source, i just gave no and it got installed. I guess you can take that method if nothing else seems to work.

Just so everyone knows, if you install Gdebi Package Installer, you aren't bothered about any of this stuff.  Just a tip. :)

---

### Post by josephks on 2011-11-29
> **ranjit. said:**
> i found that useful, but just in case that doesnt work you  can install it via terminal, i got a similar issue when i tried to install grub-customizer, i just typed sudo apt-get upgrade grub-customizer and they it asked weather to verify the source, i just gave no and it got installed. I guess you can take that method if nothing else seems to work.

This does not solve the underlying problem, which is that someone maybe monkeying with the packages and I won't know it because I can't verify the signatures.  Are the packages in the ubuntu repos not signed, or is there something wrong on my end?

This is what I am seeing:

```

root@jks-laptop:~# apt-get install update-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  update-manager-core
The following packages will be upgraded:
  update-manager update-manager-core
2 upgraded, 0 newly installed, 0 to remove and 365 not upgraded.
Need to get 816 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  update-manager-core update-manager
Install these packages without verification [y/N]? n
E: Some packages could not be authenticated
root@jks-laptop:~# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.04
Release:    11.04
Codename:    natty


```

---

### Post by Jesua on 2012-02-15
This worked for me...

1. Uncheck all the sources options.
2. Save changes
3. Check them again.
4. Save changes

It is necesary to check the sources indicated on this topic and is better to work with the Synaptic.

---

### Post by timbck2 on 2012-03-20
> **Jesua said:**
> This worked for me...

1. Uncheck all the sources options.
2. Save changes
3. Check them again.
4. Save changes

It is necesary to check the sources indicated on this topic and is better to work with the Synaptic.

This worked for me as well.

---

### Post by hypnojelly on 2012-05-25
> **binarylife said:**
> Yeah , I did almost the same . And it works fine with no problems .Anyway thank you Sam . : )
 
Ditto. :)

---

### Post by oldos2er on 2012-05-25
Old thread closed.

---

