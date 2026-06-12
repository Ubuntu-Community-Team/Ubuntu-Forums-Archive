---
title: "Canon i560 Printer"
date: 2010-06-02
forum: General Help
---

### Post by ibates on 2010-06-02
I have been struggling with less than perfect printer drivers for some time using Ubuntu 7.x, 8.x and 9.x.  But yesterday I installed 10.04 LTS.  After some initial installation problems (see threads below), it is up and running at 1 million miles per hour and looking good.  There seem to be many very nice refinements.

But the one affecting printing with my Canon i560 Inkjet printer is one of the nicest.

To install this printer, merely select "Printing" from the System->Administration menu and fill in the spaces.  Make sure the printer is on line.  It worked for me first time, perfectly.

What a pleasant surprise.

---

### Post by loro on 2010-06-11
Hello! your driver for the canon i560 printer is also the one for the canon i950 printer to install on ubuntu 10.04 and the procedure to install it is the same as you explain in your post and I just want it to complement it.
after many intents to get support and install my canon i950 printer on ubuntu I found this site in spanish that saved me the day and I thank the web owner's post for that help guide at:
[http://www.tuxapuntes.com/drupal/node/1378](http://www.tuxapuntes.com/drupal/node/1378)
Since some canon drivers are not even in the list of repositories I just opened the terminal and typed;

sudo gedit /etc/apt/sources.list

and then added the following line at the new window that opened which contains the repositories list and at the bottom I pasted it then I saved the list and closed it.
the line I pasted at the list is:

deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./

the At the terminal I typed:

apt-get install libcnbj-2.2 bjfilter-2.2 pstocanonbj

which are repositories that make work this following printers:
Canon Pixus 550i / 850i / 950i (i550 / i850 / i950) and iP90 Driver as specified by the post at this site:
[http://www.tuxapuntes.com/drupal/node/1378](http://www.tuxapuntes.com/drupal/node/1378)

After I typed the above line at the terminal it just did some kind of codes by itself (I got scared) then I close it.

I reboot my laptop and plug the i950 printer usb cable and it then detected new hardware and I selected the manufacturer CANON from the list and then the drivers for the i560 since the ones for the i950 were not even displayed then I waited for it to installed and now my canon i950 works like a charm. 
I hope this can help many others that are still straggling with their canon printers. Ubuntu is amazing, good bye Microsoft windows and office monopoly, with ubuntu we now have amazing alternatives always evolving getting better all the time.\\:D/

---

