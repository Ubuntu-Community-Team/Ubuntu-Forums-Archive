---
title: "Turn off Tap To Click"
date: 2012-02-20
forum: General Help
---

### Post by Tropicalbound on 2012-02-20
I'm running Ubuntu 11.10 on a Dell Latitude and I need to turn off Tap To Click on the touchpad.  The option to turn it off does not exist in  System Settings.  Can someone point me in the right direction?

Thanks

TB

---

### Post by ajgreeny on 2012-02-20
Try synclient in terminal  ```
synclient MaxTapTime=0
``` though I think some Dell laptops have touchpads that are not or are not detected as synaptics pads.  Things then get more difficult, so lets go one jump at a time.

It it works you can make a simple script and add it to your startup applications so that it will be run at session start every time you start ubuntu.

It may help to use the listing option as well with ```
synclient -l
``` which may give you other possible options to search out in more detail

---

### Post by Tropicalbound on 2012-02-20
Thanks for the reply, ajgreeny.

I ran synclient MaxTapTime=0 and the reply states:

Couldn't find synaptics properties.  No synaptics driver loaded?

I did a search, but came up empty on driver possibilities.

TB

---

### Post by ajgreeny on 2012-02-20
> **Tropicalbound said:**
> Thanks for the reply, ajgreeny.

I ran synclient MaxTapTime=0 and the reply states:

Couldn't find synaptics properties.  No synaptics driver loaded?

I did a search, but came up empty on driver possibilities.

TB
That's Dell for you, I'm afraid.  See what ```
xinput list
``` says about the mouse/touchpad hardware on the laptop, and we'll go from there.

---

### Post by Tropicalbound on 2012-02-20
The results of lshw is attached.  Probably much more information than you needed.

Thanks again for your help.

TB

---

### Post by ajgreeny on 2012-02-20
> **Tropicalbound said:**
> The results of lshw is attached.  Probably much more information than you needed.

Thanks again for your help.

TB
Sorry, but I edited my post to command ```
xinput list
``` after you last looked at it.  Can we see output from that please.

I realised too late that **lshw** didn't help

---

### Post by Tropicalbound on 2012-02-20
No Problem.  That output is a little more manageable anyway....


Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 ALPS GlidePoint                  	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_HD             	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=13	[slave  keyboard (3)]


TB

---

### Post by Tropicalbound on 2012-02-20
Oh, and if turning off Tap to Click doesn't seem feasible, is it possible to turn off the entire touchpad?  I'll just use a small mouse.....

TB

---

### Post by ajgreeny on 2012-02-20
> **Tropicalbound said:**
> No Problem.  That output is a little more manageable anyway....


Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 ALPS GlidePoint                      id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_HD                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=13    [slave  keyboard (3)]


TB
The first four lines of that output are obviously the touchpad, but unfortunately it doesn't help me much, as I was hoping to see something about "synaptics" in there.  However have a look at:-
[http://ubuntuforums.org/showthread.php?t=1757679](http://ubuntuforums.org/showthread.php?t=1757679)
[http://ubuntuforums.org/showthread.php?p=10651082#post10651082](http://ubuntuforums.org/showthread.php?p=10651082#post10651082)
[http://ubuntuforums.org/showpost.php?p=10651082&postcount=13](http://ubuntuforums.org/showpost.php?p=10651082&postcount=13)
> Oh, and if turning off Tap to Click doesn't seem feasible, is it  possible to turn off the entire touchpad?  I'll just use a small  mouse.....

TB 	You may be able to do that in the BIOS, but otherwise I'm not sure how you can do anything about disabling the touchpad if those posts above don't help..

---

