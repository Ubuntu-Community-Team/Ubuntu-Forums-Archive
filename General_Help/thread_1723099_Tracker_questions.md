---
title: "Tracker questions"
date: 2011-04-06
forum: General Help
---

### Post by blueridgedog on 2011-04-06
I am once again trying to get a fully functional desktop at work without a dual boot setup.  One issue is file searching. 

I have looked at beagle, tracker and Google Desktop.  I am currently testing Google Desktop and it appears to work well, but it is not integrated into nautilus and it appears to not index my email in evolution that is accessed via an exchange server.  

Beagle appears dead.

Tracker looks promising, but I can't tell if it integrates into Nautilus currently without rebuilding Nautilus.  

If you use Tracker, can you tell me how it works with Nautilus, mapped cifs drives on windows servers and evolution in exchange mode. 

Also, the current version of tracker is 0.10.6, but on 10.04 only 0.6.X is available and Natty looks poised to ship with 0.8.X.  Is there any advantage to compiling it?  Are there Ubuntu specific tweaks that are lost if you go with source?

---

### Post by ajgreeny on 2011-04-06
It seems to as far as I can tell.  I use Tracker to find content in files successfully, and until you asked I had not even thought about integration into nautilus, so thanks to your question I now know more than I did half an hour ago!  I can not answer your question on networked drives as I have none to search, but tracker only normally searches your /home by default, so I doubt it will work on anything that is not mounted permanently somewhere in your home folder, though you can add other folders if you wish in **System ->Preferences ->Search & Indexing**

As an example query, I have just searched, firstly using nautilus, for the word "nevelle" which I know appears in several invoices and accounts spreadsheets among other things on my machine, a Mr Nevelle being a customer of mine.  Nautilus found 23 files, including all those I have mentioned, which surprised me, as i thought nautilus normally only searched for file and folder names, not content.  I have always used tracker for such searches.

Using Tracker to do the same search again, the same 23 files were found.  The advantage of tracker itself is that it shows how the search term is used in the file and its full pathway, so can be more helpful than nautilus, which does not even show the pathway, it just lists the files by name.

So from that exercise I presume that if tracker is installed, it is automatically integrated into the nautilus search facility.  GREAT!!

---

### Post by DZ* on 2011-05-03
> **blueridgedog said:**
> I am currently testing Google Desktop and it appears to work well, but it is not integrated into nautilus and it appears to not index my email in evolution that is accessed via an exchange server.

I've been using Google Desktop to index Evolution IMAP email (not sure about exchange), but email needs to be stored locally, i.e. email folders properties have to be checked "for offline operation". It also indexes Kmail (offline IMAP) and is smart enough to store only one copy from either Evolution or Kmail folders (I like redundancy and bloat).

> **blueridgedog said:**
>  Also, the current version of tracker is 0.10.6, but on 10.04 only 0.6.X is available and Natty looks poised to ship with 0.8.X.  Is there any advantage to compiling it?  Are there Ubuntu specific tweaks that are lost if you go with source?

You can get a more recent one for Lucid from their PPAs
[https://launchpad.net/~tracker-team/+archive/tracker](https://launchpad.net/~tracker-team/+archive/tracker)
[https://launchpad.net/~tracker-team/+archive/tracker-unstable](https://launchpad.net/~tracker-team/+archive/tracker-unstable)

The packed ones don't index evolution emails.

---

