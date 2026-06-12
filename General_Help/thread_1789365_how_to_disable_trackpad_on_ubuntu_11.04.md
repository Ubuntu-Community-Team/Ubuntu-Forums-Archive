---
title: "how to disable trackpad on ubuntu 11.04"
date: 2011-06-23
forum: General Help
---

### Post by Xpertnoob on 2011-06-23
I am having trouble disabling my trackpad 

I want to be able to disable and re-enable it, if that is possible

I have a HP touchsmart tm2 laptop and would like to just use the touchscreen sometimes thank you for your help

---

### Post by ajgreeny on 2011-06-23
It is usually in the mouse configuration dialog, but I am not sure about 11.04, or even whether it is possible to completely disable the trackpad that way.

Alternatively open up a terminal and use the command ```
synclient -l
```to list all the commands available and you may find what you need.

---

### Post by Xpertnoob on 2011-06-23
> **ajgreeny said:**
> It is usually in the mouse configuration dialog, but I am not sure about 11.04, or even whether it is possible to completely disable the trackpad that way.

Alternatively open up a terminal and use the command ```
synclient -l
```to list all the commands available and you may find what you need.

now see that is the problem, I am a newbie to ubuntu but not computers and with that being said I checked the mouse configuration and the short answer is no, its not there
is there any way in terminal I can do it or any program/app I can download thru terminal to do it and if so 

please tell me how

---

### Post by tgalati4 on 2011-06-23
Anything happen when you hit Fn+F8?

---

### Post by Xpertnoob on 2011-06-24
nope ^

---

### Post by vivek.pandey on 2011-06-24
generally laptops come with a key for disabling and enabling trackpad (touchpad).. you dont have in yours?

---

### Post by Xpertnoob on 2011-06-24
> **vivek.pandey said:**
> generally laptops come with a key for disabling and enabling trackpad (touchpad).. you dont have in yours?

I do but since I have ubuntu the driver for it does not work 

since it was an hp driver

---

### Post by hawthornso23 on 2011-06-24
Try 

```
xinput --list
```

See if you can spot the input device you want to enable or disable. You should then be able to turn it off and on with code like

```
xinput --set-prop "PS/2 Generic Mouse" "Device Enabled" 0 
```  

and


```
xinput --set-prop "PS/2 Generic Mouse" "Device Enabled" 1 
```


If you get it to work then simply set up keyboard shortcuts with those commands.

---

### Post by inameiname on 2011-06-24
Personally, I have three functions for this in my ~/.bashrc that work great for me to turn it on and off. Just replace the "12" with whatever you get for yours using the last function, "touchpad_id":

```

function touchpad_off() 
{ 
    touchpad=12;
    xinput set-prop $touchpad "Device Enabled" 0
}

function touchpad_on() 
{ 
    touchpad=12;
    xinput set-prop $touchpad "Device Enabled" 1
}

function touchpad_id()
{
xinput list | grep -i touchpad
}

```

---

### Post by Xpertnoob on 2011-06-24
> **hawthornso23 said:**
> Try 

```
xinput --list
```

See if you can spot the input device you want to enable or disable. You should then be able to turn it off and on with code like

```
xinput --set-prop "PS/2 Generic Mouse" "Device Enabled" 0 
```  

and


```
xinput --set-prop "PS/2 Generic Mouse" "Device Enabled" 1 
```


If you get it to work then simply set up keyboard shortcuts with those commands.

this is what I got after I did xinput --list


 Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3 Finger touch             	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3 Pen eraser               	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3 Pen stylus               	id=12	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=13	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=16	[slave  keyboard (3)]

now what should I do, sorry if this is a bit of a hassle 
I'm a newbie to ubuntu

---

### Post by -kg- on 2011-06-24
Pretty much, I think what you're looking for is this:

> SynPS/2 Synaptics TouchPad

As per the instructions:

> xinput --set-prop "PS/2 Generic Mouse" "Device Enabled" 0
xinput --set-prop "PS/2 Generic Mouse" "Device Enabled" 1

Replace "PS/2 Generic Mouse" with "SynPS/2 Synaptics TouchPad" and you should be good to go.  Confirmation, anyone?

---

### Post by Xpertnoob on 2011-06-24
> **-kg- said:**
> Pretty much, I think what you're looking for is this:



As per the instructions:



Replace "PS/2 Generic Mouse" with "SynPS/2 Synaptics TouchPad" and you should be good to go.  Confirmation, anyone?

THANK YOU, now how could I set up a command for it

---

### Post by -kg- on 2011-06-25
Well, if hawthornso23 is correct, just use the commands I posted previously, replacing the information I specified, and it should work.  I would think the command would work without "sudo", since touchpad control is (or should be) user-specific, but if it doesn't work at first, put a "sudo" in front of it.

Looking at the man page for xinput, I would say that he nailed it.  The specifier "--set-prop" is defined below:

> --set-prop [--type=atom|float|int] [--format=8|16|32]  device  property
       value [...]
               Set  the property to the given value(s).  If not specified, the
               format and type of the property are left as-is.  The  arguments
               are interpreted according to the property type.

So you would be setting the properties of "SynPS/2 Synaptics TouchPad" with a "0" (off) or a "1" (on).

Get used to the man pages...they can be life savers, and are interesting in any event.  Open a terminal and type "man xinput" and check it out for yourself.  Seems xinput is a fairly powerful command.

You can use "man (whatever)" for most terminal commands.

---

