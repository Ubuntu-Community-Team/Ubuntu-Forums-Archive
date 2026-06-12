---
title: "Bangalore weather for clock applet"
date: 2009-07-14
forum: General Help
---

### Post by fundae on 2009-07-14
For some strange reason, the Locations.xml file that ships with ubuntu doesn't list Bangalore. This is quite inexplicable and not a little frustrating not just because B'lore has a large number of Ubuntu users, but also because some relatively unknown cities like Trichy and Benares are listed. 

The effect of this is that this prevents the applet from retrieving Bangalore's weather information. I've created a new Locations.xml file which contains Bangalore. Once you unzip the file and copy it over to to /usr/share/libgweather/, you can add B'lore as a location in the clock/weather applets and obtain weather and temperature reports for Bangalore.

It might be a good idea to backup your old Locations.xml file.

Enjoy!

---

### Post by cancerian1in on 2009-09-28
Hi.. 

Thanks for the file :)

I am really wondering why Bangalore not listed in original .xml file

---

### Post by abhilashm86 on 2009-09-28
> **fundae said:**
> For some strange reason, the Locations.xml file that ships with ubuntu doesn't list Bangalore. This is quite inexplicable and not a little frustrating not just because B'lore has a large number of Ubuntu users, but also because some relatively unknown cities like Trichy and Benares are listed. 

The effect of this is that this prevents the applet from retrieving Bangalore's weather information. I've created a new Locations.xml file which contains Bangalore. Once you unzip the file and copy it over to to /usr/share/libgweather/, you can add B'lore as a location in the clock/weather applets and obtain weather and temperature reports for Bangalore.

It might be a good idea to backup your old Locations.xml file.

Enjoy!

good work fundae:) so you are from bangalore!! i'm from same place, sad to see no includes in city option in most of websites and also ubuntu cd:(

---

### Post by abhilashm86 on 2009-09-28
> **cancerian1in said:**
> Hi.. 

Thanks for the file :)

I am really wondering why Bangalore not listed in original .xml file

bangalore is still not in ubuntu cd, launchpad and more appplications, very sad to see, can anyone try adding or ask administrators to give option of bangalore??

---

### Post by subramanyamn on 2009-11-03
Thanks a ton for the file, mate!

---

### Post by sharadaprasad on 2009-11-03
Hey, thanks a lot for much needed file. I replaced the file but could not access the location immediately in clock applet. Should I restart / logout/login again?

---

### Post by k.sangeeth on 2009-11-08
Thanks for the info ..
The file provided by you had the following entry for Bangalore :
<city>
 <name>Bangalore</name>
 <coordinates>13.2 77.3</coordinates>
 <location> 
  <name>Bangalore</name> 
  <code>VOBL</code> 
  <coordinates>13.2 77.3</coordinates>
 </location>
</city>

But I modified it as below :
<city>
 <name>Bangalore</name>
 <coordinates>12.966666 77.566666</coordinates>
 <location>
  <name>Bangalore</name>
  <code>VOBG</code>
  <coordinates>12.949986 77.668206</coordinates>
 </location> 
</city>

The Location code and coordinates of the modified entry is more close to Bangalore city :)

But good work done .. I was looking for these changes from a long time.

---

