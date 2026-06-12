---
title: "Software Removal"
date: 2010-03-12
forum: General Help
---

### Post by dsmithnc on 2010-03-12
Running Karmic.  I have two installations of Firefox on my laptop, One installation is keyed to: dick/.firefox 3.6 and the other is found in the normal locations; i.e. /usr/bin/firefox /etc/firefox /usr/lib/firefox /usr/lib64/firefox /usr/share/firefox.

Currently the Firefox programs seem to start in rotation, first one and if I close it, then I have to start the other.

I'd like to remove both of them completely and start over so that Firefox operates normally.

What is the right way to remove all traces of the FFX installs?

Thanks,

Dick

---

### Post by ajgreeny on 2010-03-12
I'm not quite sure what you have done other than, I presume, installing, or at least using FF 3.6, nor do I understand what you mean by "One installation is keyed to: dick/.firefox 3.6"

Is the FF 3.6 running from an executable that you downloaded from mozilla direct, and have the executable **firefox** file in the **dick/.firefox 3.6** folder?  If so it is very unusual to have a folder name with a space and a . in the name, but I have not tried 3.6 yet so am unaware of where it puts all its files.

Can you give more information about what you did and exactly why you think it necessary to completely remove all firefox instances.  If you are running 3.6 from a folder in home you can just delete the executable and folders that the 3.6 version has made upon running, but keep everything else.  Do not delete the hidden ~/.mozilla folder as you will lose all bookmarks etc from the profile if you do.

---

### Post by pricetech on 2010-03-12
> **ajgreeny said:**
> If so it is very unusual to have a folder name with a space and a . in the name,

The folder names that start with periods, commonly referred to a "dot folders" are hidden.  Same with "dot files".

---

### Post by ajgreeny on 2010-03-12
> **pricetech said:**
> The folder names that start with periods, commonly referred to a "dot folders" are hidden.  Same with "dot files".
Yes, I know that, but it is not quite what I meant regarding the filename or folder name.

I just do not totally understand what the OP meant by his question, but if the new install of FF3.6 is in his home as opposed to a proper install of a deb, all that is needed is for the folder that was extracted from the mozilla download tarball to be deleted from his home.

PS, I have now tried the new FF3.6 as a direct download from mozilla, and running from my home.  The tarball extracted to a folder simply called firefox also in home, and it contains a shellscript which starts the firefox-bin in that firefox folder; no installation is or was required.  If I deleted the firefox folder I extracted, FF3.6 would be gone totally.

---

### Post by dsmithnc on 2010-03-13
> **ajgreeny said:**
> I'm not quite sure what you have done other than, I presume, installing, or at least using FF 3.6, nor do I understand what you mean by "One installation is keyed to: dick/.firefox 3.6"

Is the FF 3.6 running from an executable that you downloaded from mozilla direct, and have the executable **firefox** file in the **dick/.firefox 3.6** folder?  If so it is very unusual to have a folder name with a space and a . in the name, but I have not tried 3.6 yet so am unaware of where it puts all its files.

Can you give more information about what you did and exactly why you think it necessary to completely remove all firefox instances.  If you are running 3.6 from a folder in home you can just delete the executable and folders that the 3.6 version has made upon running, but keep everything else.  Do not delete the hidden ~/.mozilla folder as you will lose all bookmarks etc from the profile if you do.


Thanks for the response.  I'm not sure whether I can add much light to my problem.

In my home folder I have three separate instances of firefox appearing.  one is /home/dick/firefox, one is home/dick/.firefox-3.6.2pre and one is under .mozilla.

In my software sources I have the ubuntu-daily ppa added.

Now in other locations there are entries for Firefox as well, including /usr/lib/firefox and /usr/lib64/firefox and /usr/lib64/firefox-3.6.2pre.

So, when I start firefox, I'm never sure which one starts and I have to find another that will. (does that make sense?)

Therefore I'm thinking the only way out of this mess I've gotten myself into is to remove everything related to Firefox and start over.

Hope this helps.

Dick

---

