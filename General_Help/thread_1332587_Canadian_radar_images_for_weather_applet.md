---
title: "Canadian radar images for weather applet"
date: 2009-11-20
forum: General Help
---

### Post by gramound on 2009-11-20
The weather applet doesn't seem to provide radar images for Canadian locations (from weather.com), so I wanted to use a custom URL for Environment Canada's radar images (weatheroffice.gc.ca/radar/...). Unfortunately, this URL changes every 10 minutes (filename includes timestamp).

Instead, I point the weather applet to a local php script that calculates a suitable filename and redirects to the current file on weatheroffice.gc.ca. 
It's ugly but it works for me: [ATTACH]136951[/ATTACH]

I guess a better solution would be to ask them to create a static URL and have someone integrate it in gweather-applet... ;-)

---

### Post by Billy227 on 2009-12-16
Thanks! I've been looking for a solution to this for a while, and this works great! :P

---

### Post by redace25 on 2010-01-10
Hi, I am new fairly new to ubuntu. How would you go about pointing the weather applet to the php script?

---

### Post by FraggedLocust on 2010-01-27
I'm trying file:///home/user/Downloads/ca_radar.php?region=WSO&overlays=cities,roads as my custom address, but nothing seems to be loading.

---

### Post by rescyou on 2010-03-15
You can use Accuweather radar maps:

1. Goto: [COLOR="Blue"]**[http://www.accuweather.com/canada-index.asp]("http://www.accuweather.com/canada-index.asp")**[/COLOR]
2. Click on "**Radar**" menu item and choose "**Local**"
3. Pick the radar station on the map you wish (white square).
4. On the radar map choose **Animate** 
5. Move mouse off to the side and **Right Click**, Choose **View Page Source**
6. "Find" using **ctrl+F** this: **"http://sirocco.accuweather.com"** *(without quotes)*
7. Copy the Entire URL, cut + paste into the weather applet.

My URL was: *"http://sirocco.accuweather.com/nxssa_r1_h_500x620d/r1h/inxr1CXBUa_h.gif"*

Unfortunately there are no city names on the map.

---

### Post by redace25 on 2010-03-15
Thanks for your help. It worked nicely.

---

### Post by Rowan_ on 2010-10-16
Thanks rescyou, works like a charm.

For Victoria BC the address is:
<http://sirocco.accuweather.com/nxssa_r1_h_500x620d/r1h/inxr1CXSIa_h.gif>

---

### Post by gramound on 2010-10-17
> **FraggedLocust said:**
> I'm trying file:///home/user/Downloads/ca_radar.php?region=WSO&overlays=cities,roads as my custom address, but nothing seems to be loading.

Sorry for the late reply, I didn't get the email notification. You can't run the php file directly from a file url, you need to put it in a local http server with php support. Here is a simple way to install it:
```
sudo apt-get install apache2 php5
sudo mv ca_radar.php /var/www/
```
Then you should be able to use: [http://localhost/ca_radar.php?region=WSO&overlays=cities,roads](http://localhost/ca_radar.php?region=WSO&overlays=cities,roads)

---

### Post by coldraven on 2010-10-17
Thanks for the tip, I now have my local radar map.

Intead of viewing the page source just right click on the map and select "View Image Info".
You can copy and paste the text from where it says "Location".

I just discovered that in Firefox I can highlight text like this:
Click at position on screen
Press Control+Shift+RightArrow     (this highlights to the end of a word)
Repeat RightArrow until you have selected enough.
Then as usual press Control+C to copy.

---

