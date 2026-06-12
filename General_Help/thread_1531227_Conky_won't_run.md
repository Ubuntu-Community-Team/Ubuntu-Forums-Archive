---
title: "Conky won't run"
date: 2010-07-14
forum: General Help
---

### Post by JohnDMcClane on 2010-07-14
Okay, so I've installed conky (quite a few times through various ways), and whenever I try to run it (through the Alt + F2 way, typing in "conky", without " before and after the word conky), the "Run program" screen disapears as if it's running Conky, but I can't find it on the panel or at my desktop. Is this how Conky works, or what am I doing wrong?

---

### Post by Brandon Williams on 2010-07-15
When the run dialog disappears, that doesn't mean that the program ran successfully. It only means that the program was found and run.

What happens if you run conky from the command line in a terminal? Are there any error messages?

---

### Post by JohnDMcClane on 2010-07-15
> **Brandon Williams said:**
> When the run dialog disappears, that doesn't mean that the program ran successfully. It only means that the program was found and run.

What happens if you run conky from the command line in a terminal? Are there any error messages?

> 
johndmcclane@johndmcclane-laptop:~$ conky
Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
	This program is calling the Imlib call:

	imlib_context_free();

	With the parameter:

	context

	being NULL. Please fix your program.
johndmcclane@johndmcclane-laptop:~$ 


That's what appears. Any help?

---

### Post by SonicLizzz on 2010-07-15
I'm having the exact same problem!

---

### Post by mcduck on 2010-07-15
```
Conky: missing text block in configuration; exiting
```
Well, this pretty much tells you what's the problem: your configuration file is missing something and that stops Conky from running.

Check the config file and try again.

---

### Post by stinkeye on 2010-07-15
Running "conky" in terminal will use the config file **~/.conkyrc**
If you have no ~/.conkyrc it will use the default config at **/etc/conky/conky.conf**


If, when you run in the terminal```
conky -c /etc/conky/conky.conf
```
you see the attached pic in the top left corner
then your conky config at ~/.conkyrc is faulty.


You can run any config you download using
```
conky -c [COLOR="Blue"]/path/to_any/downloaded/config[/COLOR]
```

---

### Post by JohnDMcClane on 2010-07-15
> **stinkeye said:**
> Running "conky" in terminal will use the config file **~/.conkyrc**
If you have no ~/.conkyrc it will use the default config at **/etc/conky/conky.conf**


If, when you run in the terminal```
conky -c /etc/conky/conky.conf
```
you see the attached pic in the top left corner
then your conky config at ~/.conkyrc is faulty.


You can run any config you download using
```
conky -c [COLOR="Blue"]/path/to_any/downloaded/config[/COLOR]
```

Yeah, I got the attached image appearing. What exactly is it you mean I should do then? And thanks for helping :)

---

### Post by stinkeye on 2010-07-16
> **JohnDMcClane said:**
> Yeah, I got the attached image appearing. What exactly is it you mean I should do then? And thanks for helping :)
Conky only comes with a very basic config (/etc/conky/conky.conf). For conky to look like pics you may have seen you have to download the config for that particular display or create your own config. See the link below for pics and configs.

Normally, even after you have installed conky, you do not have a .conkyrc file (hidden file in your home folder...ctrl+h to show hidden files).
Usually your ~/.conkyrc is a config you have made yourself or downloaded from places like [**_[COLOR="DarkRed"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865"). 
I would say you have downloaded someone's conky config and saved it in your
home folder as **.conkyrc**
This is all perfectly normal and the correct way to do things so that when you enter conky in the terminal it will load this file.

If you want to use the config at **~/.conkyrc** (~ is short for */home/your_username*) post the contents of this file 
so i can have a look at it.

One problem could be the conky config may be using things like embedded images or lua which the standard conky package doesn't support.

I would suggest opening software centre and do a search for conky.
Uninstall **conky**
and install the **conky-all** package, which has been compiled with more options. 

Now, enter **conky** in the terminal and see if the config at ~/.conkyrc displays.
If not post the contents of your ~/.conkyrc

Also I would have a look at this conky tutorial.
[**_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

---

### Post by Brandon Williams on 2010-07-16
```
Conky: missing text block in configuration; exiting
```

The conky config must contain a line that that says "TEXT", followed by the details of exactly what you want to see on the screen. Your configuration does not have such a line or the specifications of expected output.

When you look at sample .conkyrc files, look for the line "TEXT" and examine all the code that follows this line.

Here is a very simple example:
```
TEXT
SYSTEM INFO
${hr}
Local time:$alignr ${time %d-%b-%Y %H:%M}
Host:$alignr $nodename
${if_up eth0}Address:$alignr ${addr eth0}
${endif}${if_up wlan0}Address: $alignr${addr wlan0}
Wifi Network:$alignr ${wireless_essid wlan0}
${endif}Kernel:$alignr $kernel
RAM:$alignr $mem/$memmax
Swap usage:$alignr $swap/$swapmax
Disk usage:$alignr ${fs_used /}/${fs_size /}
CPU usage:$alignr ${cpu cpu0}%/${cpu cpu1}%
```
If you add this at the very end of your .conkyrc file, then conky will display some basic system information.

The beginners guide referenced earlier will give you a lot more detail about this and the conky config in general.

---

