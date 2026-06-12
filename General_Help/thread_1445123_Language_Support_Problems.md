---
title: "Language Support Problems"
date: 2010-04-02
forum: General Help
---

### Post by nicknefarious on 2010-04-02
Hi all,

I have been trying to activate iBus and install Chinese Language packs on my reasonably new Karmic 64-bit install. When I go to the Language Support in the Administration menu I get a message saying that...

> **[SIZE="2"]Language support is not installed completely[/SIZE]**. Some translations or writing aids available for your chosen languages are not installed yet. Do you want to install them now?

I have the option to be reminded later or install them now. Choose install them now and I get a new message.

> Could not apply changes. Fix broken packages first!

In the details of the error messages these are the packages that are listed....

[B]thunderbird-locale-en-gb
gimp-help-en
kde-l10n-engb
gnome-user-guide-en
openoffice.org-help-en-gb
openoffice.org-l10n-en-gb
language-pack-kde-en
openoffice.org-l10n-en-za[/B]

I have scoured Synaptic for each, and none are installed. I have run the broken packages fix and also followed another guide which did not work which suggested running a few commands...

```
sudo apt-get -configure -a
```
```
sudo apt-get -f install
```
```
sudo apt-get --fix-missing install
```
```
sudo apt-get clean
```
```
sudo apt-get update
```

The sudo apt-get update returned an error that disappeared after re-rerunning it again and the first configure command returned a small error too about not understanding the code and then

> E: Opening configuration file onfigure - ifstream::ifstream (2: No such file or directory)

After all of these still no joy. It will not fix the problem. If I ignore the problem and move on to the next box and select ibus as the input method and go select Add a new language and choose Chinese the language support box greys out and remains this way eternally (until I go into the process in System Monitor and manually kill it.

Can anyone help me out here please?

Cheers and thanks,

Nick

---

### Post by nicknefarious on 2010-04-18
No-one out there is able to give me any help on this?

Also the last couple of times I have run the Update Manager I am getting these error messages back. 

> W: Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/karmic/Release.gpg](http://mirror.pacific.net.au/linux/ubuntu/dists/karmic/Release.gpg)  Could not connect to mirror.pacific.net.au:80 (61.8.0.17), connection timed out

W: Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/karmic/main/i18n/Translation-en_AU.bz2](http://mirror.pacific.net.au/linux/ubuntu/dists/karmic/main/i18n/Translation-en_AU.bz2)  Unable to connect to mirror.pacific.net.au http:

W: Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/karmic/restricted/i18n/Translation-en_AU.bz2](http://mirror.pacific.net.au/linux/ubuntu/dists/karmic/restricted/i18n/Translation-en_AU.bz2)  Unable to connect to mirror.pacific.net.au http:

W: Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/karmic/universe/i18n/Translation-en_AU.bz2](http://mirror.pacific.net.au/linux/ubuntu/dists/karmic/universe/i18n/Translation-en_AU.bz2)  Unable to connect to mirror.pacific.net.au http:

W: Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/karmic/multiverse/i18n/Translation-en_AU.bz2](http://mirror.pacific.net.au/linux/ubuntu/dists/karmic/multiverse/i18n/Translation-en_AU.bz2)  Unable to connect to mirror.pacific.net.au http:

W: Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/karmic-updates/Release.gpg](http://mirror.pacific.net.au/linux/ubuntu/dists/karmic-updates/Release.gpg)  Unable to connect to mirror.pacific.net.au http:

W: Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/karmic-updates/main/i18n/Translation-en_AU.bz2](http://mirror.pacific.net.au/linux/ubuntu/dists/karmic-updates/main/i18n/Translation-en_AU.bz2)  Unable to connect to mirror.pacific.net.au http:

W: Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_AU.bz2](http://mirror.pacific.net.au/linux/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_AU.bz2)  Unable to connect to mirror.pacific.net.au http:

W: Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_AU.bz2](http://mirror.pacific.net.au/linux/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_AU.bz2)  Unable to connect to mirror.pacific.net.au http:

W: Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_AU.bz2](http://mirror.pacific.net.au/linux/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_AU.bz2)  Unable to connect to mirror.pacific.net.au http:

W: Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/karmic-security/Release.gpg](http://mirror.pacific.net.au/linux/ubuntu/dists/karmic-security/Release.gpg)  Unable to connect to mirror.pacific.net.au http:

W: Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/karmic-security/main/i18n/Translation-en_AU.bz2](http://mirror.pacific.net.au/linux/ubuntu/dists/karmic-security/main/i18n/Translation-en_AU.bz2)  Unable to connect to mirror.pacific.net.au http:

W: Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_AU.bz2](http://mirror.pacific.net.au/linux/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_AU.bz2)  Unable to connect to mirror.pacific.net.au http:

W: Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/karmic-security/universe/i18n/Translation-en_AU.bz2](http://mirror.pacific.net.au/linux/ubuntu/dists/karmic-security/universe/i18n/Translation-en_AU.bz2)  Unable to connect to mirror.pacific.net.au http:

W: Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_AU.bz2](http://mirror.pacific.net.au/linux/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_AU.bz2)  Unable to connect to mirror.pacific.net.au http:

W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/Release.gpg](http://packages.medibuntu.org/dists/karmic/Release.gpg)  Could not connect to packages.medibuntu.org:80 (88.191.82.11), connection timed out

W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_AU.bz2](http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_AU.bz2)  Unable to connect to packages.medibuntu.org http:

W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_AU.bz2](http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_AU.bz2)  Unable to connect to packages.medibuntu.org http:

W: Some index files failed to download, they have been ignored, or old ones used instead.


I have tried a number of different servers but with no luck. I can see language packs amongst this. Is this problem linked?

If not any ideas what is going on here?

Please...

Thanks,

Nick

---

### Post by nicknefarious on 2010-04-25
Fixed the downloads for update problem but still no solution for the Language Support Problems. It is preventing me from installing new language packs as, when I choose a language pack to install, it says it is going about this but it actually seems to be doing nothing. I have left it running for a long time and still it seems to be unable to complete the task. I can't kill it either once it is started. The only way to stop the process is to restart.

Anyone any ideas?

Thanks,

Nick

---

### Post by michwe on 2010-05-03
I have the same problem. The commands above don't work for me neither. I just want to say, that you are not the only one having this problem. However I just installed Ubuntu Version 10.04 and it is the first time this problem occurs. 

A second install of Ubuntu showed, that the setup procedure is able to fetch the approbriate packets from the internet, while the PC is connected to the Internet during installation. Maybe this helps to find a solution.

---

### Post by nicknefarious on 2010-05-03
Thanks for your info. Anyone else can weight in here as to what the problem is and/or how to fix it?

This has been going on for quite a while now.

Any help would make me atleast a little happy...

Nick

---

### Post by AlexDudko on 2010-05-04
No help or fix - just tried to purge all Russian language support files and install them again - no effect.

---

### Post by AlexDudko on 2010-05-05
It turns out there's no full language support for Russian. The package "language-support-input-ru" isn't installable - there's no such a package in [repositories]("http://91.189.94.219/lucid/translations/").

---

### Post by zaphod777 on 2010-05-05
try installing them from synaptic. When I type "Chinese" into the search I can see all of the language packs and input methods. Not sure which Chinese you need "simplified" or one of the others.

---

### Post by AlexDudko on 2010-05-05
There's no such a package (language-support-input-ru) in Synaptic.

> $ aptitude search language-support-input-ru
c   language-support-input-ru       - Input methods metapackage for Russian
> $ aptitude show language-support-input-ru
No current or candidate version found for language-support-input-ru
Package: language-support-input-ru
State: not installed
Version: 1:9.10+20090909
Priority: optional
Section: translations
Maintainer: Language pack maintainers <language-packs@ubuntu.com>
Uncompressed Size: 41,0k
Depends: im-switch
Description: Input methods metapackage for Russian
 This metapackage depends on input method packages which might be useful in a
 Russian language environment. 
 
 If you also want your applications and the desktop to be translated, please
 additionally install language-pack-ru. 
 
 Language: Russian

There was the package in Ubuntu-9.10 but current stable (10.04) doesn't have one.

---

### Post by nicknefarious on 2010-08-11
Don't know if it's any help to anyone but I went back to the language administration and tried to install what I wanted and everything went smoothly and I now have iBus and all the language input methods I want up and running. Don't know what changed or fixed it but it is. I did nothing.

Nick

---

### Post by nicknefarious on 2010-08-29
AAahhhhhhhh... <-(pulling hair out by roots)

I have just re-installed Lucid 64-bit on my laptop and the Language Support issue has returned. exactly the same as before, the error messages and the packages ( a list below ).

[B]thunderbird-locale-en-gb
gimp-help-en
kde-l10n-engb
gnome-user-guide-en
openoffice.org-help-en-gb
openoffice.org-l10n-en-gb
language-pack-kde-en
openoffice.org-l10n-en-za
openoffice.org-hyphenation
openoffice.org-hyphenation-en-us
openoffice.org-thesaurus-en-au
openoffice.org-thesaurus-en-us[/B]

Again I tried running the 'fix broken packages command from the synaptic packager menu, and it just says fixed all broken dependencies. But the problem remains.

When I go into Synaptic and try to install each of the packages individually I get an error message:-

> The following packages have unresolved dependencies. Make sure that all required repositories are added and enabled in the preferences

and then this

> thunderbird-locale-en-gb:
  Conflicts: thunderbird (>3.1~a1) but 3.1.1+nobinonly-0ubuntu1~10.04~ricotz1 is to be installed

Obviously this error message was returned when trying to install the first of the packages **thunderbird-locale-en-gb**

All of the packages except this thunderbird package I was able to install individually using synaptic package manager. If you can't remember the names of the packages try running the language support action again and then read the details of the error message. It will list all of the problematic packages for you and then you can try installing them each individually. A pain in the ..... I know... but all installed for me except for the thunderbird package above.

When trying to force install it I get this error message below. Please can someone help me resolve this. This bug or whatever it is has existed for a long time and seems to remain unresolved still.

> xxxx@xxxx-laptop:~$ sudo apt-get install -f thunderbird-locale-en-gb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  thunderbird-locale-en-gb: Conflicts: thunderbird (> 3.1~a1) but 3.1.1+nobinonly-0ubuntu1~10.04~ricotz1 is to be installed
E: Broken packages
xxxx@xxxx-laptop:~$ 

Thanks,

Nick

---

### Post by Treb on 2010-08-30
Hi Nick,

I have exactly the same problem.

Here's what I did:
- uninstall Thunderbird
- let Ubuntu fix the other errors -> works
- reinstall the correct version -> problem still exists

After that I upgraded to the latest FF beta via **ppa:ubuntu-mozilla-daily/ppa**
But the same error occurred.

So, still no solution on this side: anybody?

Thanks,

Bert

---

### Post by nicknefarious on 2010-09-06
Finally after (as described previously in this thread) I installed all the packages I could manually (I used synaptic) I was left with this one thunderbird-locale-en-gb and it would not install due to conflicts. I believe for some reason it was conflicting with the version of thunderbird.

Anyway I found this PPA with latest version of thunderbird-locale-en-gb so I added the PPA

```
sudo add-apt-repository ppa:eugenesan/mozilla 
```

and then aptitude updated

```
sudo aptitude update
```

and then went into synaptic and located the newer version of the package (thunderbird-locale-en-gb) and installed it no problem. When I went back to the language support it tossed a new error at me this time for thunderbird-locale-en-us but I was able to click on it and select install it and it installed no problem. I was then able to get back into the language support manager and select my Chinese language packages to install.

I will also remove the PPA for now until I have a little more time to check it out and see what other packages it might contain. My language packs are downloading and, fingers crossed, installing now. If any further problems I'll post back.

Hope this helps someone out. I found it by Googling the package name and found this at the top of the list - [http://www.ubuntuupdates.org/packages/show/248338]("http://www.ubuntuupdates.org/packages/show/248338")

---

