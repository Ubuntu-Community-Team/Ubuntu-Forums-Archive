---
title: "Internet Problem Just In Dapper -plz Help-"
date: 2006-06-05
forum: General Help
---

### Post by medya on 2006-06-05
I have ADSL internet ,I have ethernet modem with LAN Card.

it worked so beautifully in Breezy , and it worked well in LIVE CD and in first boot of Dapper .but now it wont connect to internet anymore 

I have collected some infromation that u may use it to fix it.

1- the Net Speed Aplet shows my internet as a PPP (dail up) while it used to show it as ETH0 in my breezy and I cant not change it to eth0 (as I was able to do in Breezy) 
2- I can connet to internet by some tricks  ,
I connect to a SSH PROXY , with this command
ssh -L 8213:localhost:8213 fred@205.234.206.139

and I force programs to use that proxy (localhost:8213)... (but the proxies are slow you know...  and I cant force all the programs to use proxy)
so I DO HAVE INTERNET but the ubuntu dapper doenst know how to use it...

I think u can find the problem .... by this thing that I found out .

3- on dapper's start up it takes much time in Configuring Netwrok interface 
there should be a problem there


I am sure many others have the same problem ...because i reinstalled dapper and the same thing happened again..

+ by the way , why ppl hadnt reported this BUG before the official release of dapper?

---

### Post by woopud on 2006-06-05
I've had a similar problem with Dapper (beta version) internet worked fine all the time for months and then suddenly it stopped working, rebooting several times, nothing helped.  I was dual booting with Windows and internet always worked in Windows but not in Dapper, I also have DSL via a network cable.  I ended up reinstalling Dapper, and then it happened again so I got rid of it all together.  I want to try dapper again.

Bert

---

### Post by medya on 2006-06-05
if they dont fix this problem, I will go back to windows, I already put a lot of time learning linux.... and still most of my hardware doesnt work 
printer Epson lx-800 
webcam
dial up winmodem
tv tuner SAA7130

+yahoo messenger with Cam and Voice
+WMV files

linux is not all Fun.

---

### Post by Patrick-Ruff on 2006-06-05
well, dialup is expected not to work, you know, there is an alternative, if you have 2 computers... you can have the Windows comp constantly running, connected to the internet, then you can run a LAN cable to the peer computer (the linux one) and then you can turn on ICS on the windows comp, that would mean setting up a small network and all that, and then making the lan DCHP on the peer computer, and viola, internet! thats how I have dialup on my Linux laptop. however, if you require the ethernet for internet, I suggest you get a router. :). that should solve your problem entirely.

---

### Post by Ramaddan on 2006-06-05
Hi,

I actually never bothered using the manual way of ADSL internet in Ubuntu,
all I did was download and run this program from roaring penguins.

[http://www.roaringpenguin.com/penguin/open_source_rp-pppoe.php](http://www.roaringpenguin.com/penguin/open_source_rp-pppoe.php)

It's a gui for ADSL connections. Very easy to use.

If you follow the install instructions, just make sure you replace version
number 3.6 with 3.8 (I don't think they updated the instructions file).

Also, make sure you try running the program in the terminal first,
because sometime the menu item made by it does not work properly,
because they didn't update the version number, which you can easily do.

I'm saying you should try it in the terminal first because it will give you
error messages if there are any, and it makes you realize whether the
problem is from the program, or menu.

Oh yeah, this program gives you internet on demand. What I mean by that is that if you want the
internet, you click on the program in menu, and it will give you a gui, then you can click on START,
and the internet will turn ON, and when you're done, you click on STOP, and it turns OFF.

I placed the menu icon on my panel, which makes it very easy, and once I turn the internet ON,
I leave it ON till I shutdown the computer. You don't need to turn it OFF.

Also, one the internet is ON, you can close the GUI, and the internet will stay ON.

Hope this helps.

---

### Post by medya on 2006-06-06
where is the Dapper Masters ? arent you responsible?

---

### Post by medya on 2006-06-06
please somebody solve this Bug... is there any way to recover the Breezy's pppoe ? and replace it with Dapper's pppoe ?

---

