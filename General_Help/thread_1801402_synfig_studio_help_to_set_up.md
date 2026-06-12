---
title: "synfig studio help to set up"
date: 2011-07-10
forum: General Help
---

### Post by porge on 2011-07-10
I'm a new to ubuntu / trying to install (build?) synfig studio in ubuntu 11.04. I've read the info from the download pages, have searched forums but nothing seems to apply to the year 2011 and ubuntu 11.04 OR my v. low level of expertise.  I'm at a loss. Any help anyone can give me is appreciated. Maybe I'm making it harder than it is. Lead the way.

---

### Post by porge on 2011-07-12
The solution: 

I downloaded all of the zip programs. There are four. 

Before I could do anything I had to install Gdebi Program Installer. This may be found in Ubuntu software. It was for me. Other wise that bit you may have to google/find and possibly load through the terminal. 

These are the downloads for Unbuntu 

ETL-0.04.13.tar.gz
synfig-0.62.02.tar.gz
synfigstudio-0.62.02.tar.gz
synfigstudio_0.63.00-20110605.master.8_i386.deb 

--------------------

note: when I tried a 64 download I got an error 'wrong architecture 'amd64'. I threw that one in the trash, dumped all of the trash and downloaded the i386. 

-----------------

In order for me to extract the files I had to right click on each file/go to permissions and allow executing file as program. 

Starting with ETL and going down the list of tars.

Right click on file/properties/permissions/allow executing file as program/close
Right click on file open with Archive Manager.
You will see the file you're trying to open
Once in Archive Manager tell it where you want it to open. 

Create a folder in the home directory under your name. In my home folder I have my name plumly and I called my new folder synfig studio.

In the location field within the Archive Manager I put /plumly /synfig studio


Again - it looked like this &#8211; Location:   /plumly/synfig studio

Then I clicked extract

On the next screen that popped up I clicked extract again. 
Then I closed all screens. 

All tars were done like this. All tars loaded into my new folder.

Last to open was the program. I right clicked/go to permissions/allow executing file as program - like all the others. Then I closed out. 

Right clicked. Told it to  'open with' - Gdebi program installer (which I had previously installed)

It takes off from there. God forbid I've left something out. There may have been an easier way but this is how I muddled through.

---

### Post by genete on 2011-07-18
To use Synfig Studio with Ubuntu 11.04 the best and easier option is to download the debian packages from here (please select your correct architecture):
[http://synfig.org/cms/en/download/stable](http://synfig.org/cms/en/download/stable)
The known problems of the Ubuntu Software center should be now fixed.

-G

---

