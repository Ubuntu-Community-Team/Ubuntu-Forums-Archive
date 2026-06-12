---
title: "Recovering files from botched 10.04 update"
date: 2010-07-09
forum: General Help
---

### Post by fieroguy19 on 2010-07-09
So when upgrading to 10.04 there were a few errors and now the machine will not boot up. All I am trying to do now is recover some pictures from the HD so I can to a clean install. I used the Ubuntu 9.04 install disk to gain access to the HD and was able to backup some of the files but other files are locked somehow. When trying to copy them it says that "folder content could not be displayed. You do not have the permission necessary to view the contents." The files in question have orange X's on them.

Is there any way to gain access to these files in question? Any help would be greatly appreciated.

Thanks

---

### Post by 23dornot23d on 2010-07-09
Type

gksudo nautilus

in a terminal ..... you should be able to get to the files then ...... without having orange crosses on them.

_______________________________

There are other ways too - so if you still have problems let us know ....... how big a drive do you have and
how is it set up ....... 

Maybe a clean installation in another partition might be useful    ....  having a separate home partition when
you do your initial setup/installation makes things easier too ..... 

but get what you want off the drive first ...... 

Depending on how much data we are talking about you getting off here ....... could can change the way
I would go about doing this .......... if its 100 photos ..... or thousands ...........

---

### Post by fieroguy19 on 2010-07-09
So I tried this and found the photos on the HD and I can see them unlike before. However when I try to copy them over to an external HD it says that "error while copying the folder cannot be handled because you do not have permission to read it." 

I feel like I am really close but it still does not work. Am I doing something wrong?

---

### Post by 23dornot23d on 2010-07-09
If you use the (gksudo Nautilus window) to copy the files to your destination drive ...... it should work as long as you have privileges to write files to your destination drive .....

Like you say you are probably very close to recovering them ...... you are very vague about your system ..... the size of the hard drive ...... the amount of data you need to recover ........ etc ...... you should keep a backup of important data as you probably know now ..... 
( I recommend using a USB hard drive for photos etc ... cheapest way of storing data per MB in my opinion )

More info might give us more options ...... 

Did you try installing UBUNTU again from a CD - (Thing to do first is get a backup of all your important DATA)  ...... by choosing empty space on the drive you may be able to get to the data once you have a OS installed and working .......  which live CDs do you have .......

If you are running from the LiveCD ..... make sure that the place you are trying to copy to is the new Hard Drive and that you have write privileges to it ........... right click on the drive and choose a folder and check the properties - permissions ......... 

should look something like this

[IMG]http://i26.tinypic.com/23t2oag.jpg[/IMG]

Just make sure that you have write access to it .... and can create files
on it .

---

