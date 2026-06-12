---
title: "How to change locale from &quot;en_US.utf8&quot;"
date: 2010-07-21
forum: General Help
---

### Post by septekin on 2010-07-21
Would someone please let me know how to change the default locale in Ubuntu 10.04.

In System/Administration/Language Support both Language and Text have been set to English (Denmark).
/etc/default/locale entry is LANG="en_DK.UTF-8".
/var/lib/locales/supported.d/locale entry is en_DK.UTF-8.

Yet locale command lists LANG=en_US.utf8, and all LC_ entries as "en_US.utf8".

The machine has been reset many a time.

Thanks in anticipation!

teoman

---

### Post by deathadder on 2010-07-21
Hi,

AFAIK locals don't get generated on each boot, have you run local-gen (as root??) since changing your settings?

---

### Post by septekin on 2010-07-21
Yes, I have. It listed en_DK.UTF-8 as up-to-date.
By the way, I have Hardy and Jaunty installed on this same laptop, they both behave good.

---

### Post by jimmers on 2010-07-21
You could try this tip:-

                                       **_Tip #3 - Getting rid of unnecessary locale data_** - For this tip, you need to download the "localepurge" package found in Synaptic Package Manager. "localepurge" is just a simple script to recover diskspace wasted for unneeded locale files and localized man pages. It will automagically be invoked upon completion of any apt installation run.

To open Synaptic Package Manager, follow the instructions in Tip #1. After opening up Synaptic Package Manager, click the **Sections** button on the bottom left hand corner of the window, if it is not already clicked. Next, at the top of the Synaptic Package Manager window, click the **Search** button. In the search window, key in the following text :
    Quote:
                                              localepurge 
                          Did the "localepurge" package popup in the package window? It probably did, unless you do not have the correct Repositories. Now, click on the box next to the "localepurge" package name. Click on **Mark for Installation**. Now click the **Apply** button at the top of the window and wait for the downloading and installing of the "localepurge" package to finish. Once it is done, a new window should popup that has a bunch of abbreviations on it. for example: 
    Quote:
                                              en
fr
po
sp
ka
etc... 
                          You want to select the abbreviation of the language that you speak, or use with Ubuntu, ignoring the capitalized ones. For example, I speak english, so I would select the "en" abbreviation. A french speaker would select the "fr" abbreviation. So on and so forth... Then click next. All done! 



Try at your  own risk, it worked me, may not for you.


Luck

---

### Post by septekin on 2010-07-21
Thanks for your tip jimmers. However, my problem is not superfluous locale data. I am taking the advice at the bottom of Synaptic's description of localepurge: ..simply don't use this package.

---

### Post by dcstar on 2010-07-22
> **septekin said:**
> Would someone please let me know how to change the default locale in Ubuntu 10.04.

In System/Administration/Language Support both Language and Text have been set to English (Denmark).
/etc/default/locale entry is LANG="en_DK.UTF-8".
/var/lib/locales/supported.d/locale entry is en_DK.UTF-8.

Yet locale command lists LANG=en_US.utf8, and all LC_ entries as "en_US.utf8".

The machine has been reset many a time.

Thanks in anticipation!

teoman
Try:
```
sudo dpkg-reconfigure locales
```
and:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_locales_to_Ubuntu_the_command_line_way](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_locales_to_Ubuntu_the_command_line_way)
[http://www.ubuntugeek.com/how-to-select-and-generate-locales-on-ubuntu.html](http://www.ubuntugeek.com/how-to-select-and-generate-locales-on-ubuntu.html)

---

### Post by septekin on 2010-07-22
Thank you dcstar. I'd already tried dpkg-reconfigure locales with no luck. I've just checked the two articles, they don't suggest anything that I have not already tried.
However, my locale now is listing correctly, after I put a line in /etc/bash.bashrc that reads "source /etc/default/locale", thanks to an article by jered of slicehost! Since the command locale is giving the right result now I have to mark this thread as solved although my real problem is not: both Firefox and Thunderbird are still conforming to the US format.

Thanks to all who tried to help.

---

### Post by lancelotj on 2011-06-19
I have the same problem in ubuntu 10.04:
[http://ubuntuforums.org/showthread.php?p=10956239#post10956239](http://ubuntuforums.org/showthread.php?p=10956239#post10956239)

And finally it is resolved in [https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/666565](https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/666565).

---

