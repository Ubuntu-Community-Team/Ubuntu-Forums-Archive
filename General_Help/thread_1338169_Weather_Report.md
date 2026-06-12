---
title: "Weather Report"
date: 2009-11-26
forum: General Help
---

### Post by Mr Nemo on 2009-11-26
Anyway to add a location to Ubuntu weather report? Any guide that I found either didn't work or was too confusing.

---

### Post by leveliv on 2009-11-26
add it to panel right click on then click preferences :P then onto the Location tab then find your place :P

---

### Post by Mr Nemo on 2009-11-26
I should clarify. My location is not on the list and I wish to add it. I know I have to edit Locations.xml in /usr/share/libgweather but I can't make heads or tails of the format all the information should be in.

---

### Post by Mr Nemo on 2009-11-26
Never Mind I figured it out. If anyone would like to know please ask. It's fairly simple.

---

### Post by fontis on 2010-06-17
> **Mr Nemo said:**
> Never Mind I figured it out. If anyone would like to know please ask. It's fairly simple.

Please share with me :(

---

### Post by Mr Nemo on 2010-06-17
Youll need an XML editor. mlview should work fine (you can find it in the repositories). Open up Locations.xml which is found in /usr/share/libgweather. Look at a few entries so you can get the basic idea of how each one is set up. Basically copy a whole entry from <city> to </city>. Paste into where you want to add a new entry. Each city is categorized alphabetically under their state (which is also categorized alphabetically), so find your state and add the new city where it should be so you can find it later on in the drop down menu. Now all you have to do is change the information in the fields. For the <code> field youll want to search for a nearby city to you and copy those letters and coordinates. Youll have to use google to get the coordinates for your own city. Do this as root (sudo) and save. Basically youll retrieve weather information from the local weather center that you specify (That's what the letters and coordinates are for). Restart the weather applet and you should be able to find the name of your city where you placed it in the list. If this wasn't clear (i'm very bad at trying to explain things in forums) let me know and ill try to clean it up a bit.

---

