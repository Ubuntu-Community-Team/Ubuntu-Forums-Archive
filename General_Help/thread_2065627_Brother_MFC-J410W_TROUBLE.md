---
title: "Brother MFC-J410W TROUBLE"
date: 2012-10-02
forum: General Help
---

### Post by NewbieToThis on 2012-10-02
[FONT=Calibri][SIZE=3]I have installed 12.04 LTS on my Toshiba 32 bit Satellite –A135 laptop. At first I was unable to recognize my Brother MFC-J410W printer after some reading and trying different options I was able to get the printer to work both via USB and wireless…..YEA!! I am unable to scan either by USB or wireless. I have been working with the Brother help desk but still no joy. Can someone please shed some light on my problem?!! Thanks. [/SIZE][/FONT]

---

### Post by kurt18947 on 2012-10-02
Setting up a Brother scanner is a bit of a job.  I've seen two issues with Ubuntu systems.


[LIST=1]
[*]There is a flaw in the installer where it puts certain files in the wrong place.  The 4th item at this Brother site addresses it: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html)
[*]SUDO users can scan but normal users cannot.  The fix is here:  [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html)
[*]To be able to scan over a network, you must enter at least one line via terminal. Here is the page for that:  [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html)
[/LIST]
I hope this will help.  Brother does have quite good linux support compared to most manufacturers except HP.   These are the two manufacturers I look at first when looking for prints or Multi-functions.

---

### Post by NewbieToThis on 2012-10-02
KURT,
Thank you I think after reading the directions the umpteenth time I believe I found my error, it was the placement of the command line. 
 
**[COLOR=black][FONT=Times New Roman][FONT=Calibri]# Brother scanners[/FONT][/FONT][/COLOR]**[FONT=Times New Roman]
**[FONT=Times New Roman][COLOR=black]ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"[/COLOR][/FONT]**
[/FONT] 
I hadn&#8217;t placed above the (Before the line "# The following rule will disable ..."): So I placed it in the correct spot and will try it when I get home from work tonight, and will post my result then. Thanks for the help and the links.

---

