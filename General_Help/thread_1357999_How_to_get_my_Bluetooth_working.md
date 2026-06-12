---
title: "How to get my Bluetooth working?"
date: 2009-12-17
forum: General Help
---

### Post by bmman on 2009-12-17
I have a Dell mini-9, running 8.04, with Bluetooth built in. I bought the netbook in the U.S. but live in Thailand. I was told once I got to Thailand that in order to get my Bluetooth connected to my cell phone I would need to download Blueman. If this is true, can anyone please tell me how to do this, or any other way to get Bluetooth up and running. 
Having zero luck in Chiang Mai,
bmman

---

### Post by fragos on 2009-12-18
you'll need to add a software source which can be done in Administration Preferences. The info you need to add is:

URI: [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu)
Distribution: karmic
Components: main

After that change, blueman will be available in Synaptic for install.

---

### Post by bmman on 2009-12-26
> **fragos said:**
> you'll need to add a software source which can be done in Administration Preferences. The info you need to add is:

URI: [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu)
Distribution: karmic
Components: main

After that change, blueman will be available in Synaptic for install.

Thanks for the help, I've been away so am just now getting back to my problem. I tried your advice but am still stuck, can you walk me through this a little more specifically? My sticking point is: There is a Preferences Tab, and there's an Administration Tab, but no Administration Preferences. Where exactly do I go to add this URL?

---

### Post by fragos on 2009-12-26
Top applet bar upper left - System-> Administration-> Software Sources-> Other Software tab-> Add button.

---

### Post by bmman on 2009-12-27
> **fragos said:**
> Top applet bar upper left - System-> Administration-> Software Sources-> Other Software tab-> Add button.

Thanks again so much. I'll have to try it tomorrow morning. Something to ponder in the meantime: I previously tried (unsuccessfully) with these directions given by another forum member:

[B]Follow these steps

Select System -> Administration -> Software Sources

Type in your password

Click on Third-PArty Software tab

Click on +Add

In the APT line, type in 
deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) hardy main 

Click on Add Source

Answer OK when it asks you to reload.

Then select System -> Administration -> Synaptic Package Manager

and search for blueman[[/B]/I][/I]

This sounds pretty similar to your recommendations, except for "deb" before and "hardy main" after the URL. When I had followed these instructions it all went fine until I got to being asked to reload. It never asked that, so I couldn't respond with "OK".
Does this sound familiar to you? What did I do/not do that was wrong?
Thanks again for any advice on this....
bmman

---

### Post by fragos on 2009-12-27
Actually his instructions are better. When in the 3rd Party, called Other Sources in new release, can you now see a line labeled blueman or with the blueman URI. It's box should be checked. Select that line and hit edit button. An edit source window will appear. For 8.04 distribution should say hardy and not karmic as I said. Note you can force a reload of repositories when you run the Update Manager with the Check button.

---

### Post by bmman on 2009-12-27
> **fragos said:**
> Actually his instructions are better. When in the 3rd Party, called Other Sources in new release, can you now see a line labeled blueman or with the blueman URI. It's box should be checked. Select that line and hit edit button. An edit source window will appear. For 8.04 distribution should say hardy and not karmic as I said. Note you can force a reload of repositories when you run the Update Manager with the Check button.

Thank you so much! It finally worked (I hadn't gone to the edit button, before). Now, maybe you can advise on what comes next? Ultimately, I need to get the Bluetooth capability on my mini-9 operational. Now that Blueman is listed in my Synaptic Manager, it needs to be installed or downloaded via a terminal, correct?

---

### Post by fragos on 2009-12-27
Run the Synaptic package manger. In the quick search window type blueman. Right click the check box which will be white because it's available but not installed. Select "Mark for installation" and click the check mark icon to Apply changes -- you may be asked to accept other changes which you should do. When the install is complete the blueman check box will now be filled green to indicate it's installed. Right click the Bluetooth icon in the applet bar and you'll be looking at blueman's options. You will need to pair/setup any Bluetooth client device you wish to access.

---

### Post by bmman on 2009-12-30
> **fragos said:**
> Run the Synaptic package manger. In the quick search window type blueman. Right click the check box which will be white because it's available but not installed. Select "Mark for installation" and click the check mark icon to Apply changes -- you may be asked to accept other changes which you should do. When the install is complete the blueman check box will now be filled green to indicate it's installed. Right click the Bluetooth icon in the applet bar and you'll be looking at blueman's options. You will need to pair/setup any Bluetooth client device you wish to access.

I seem to getting closer, but I'm not there yet. The Blueman boxes are now filled green, indicating that they were installed (there were 2), but when I rt. click the Bluetooth icon, the options I get are: Preferences, About, Send File, Browse Phone devices, Connect New Device. If I choose Browse Phone devices, my Motorola phone is listed but clicking it to connect only brings up "Couldn't display "obex://[00:21:36:26:32ADJ]/". Error: DBus error
Please select another viewer and try again."

Another viewer? I'm still confused.

---

### Post by fragos on 2009-12-30
If my memory serves me, System-> Preferences-> Startup Applications. Select entry that sys Bluetooth Manager-> Edit button-> make sure the command says "blueman-applet". Blueman replaces the default Bluetooth applet.

---

### Post by babavwoko on 2009-12-30
The blueman will not take full effect untill you restart your system cos you know during te cos of installation blueman will remove gnome-bluez which is still on your system and will purge it when you restart or you can run it trough alt+f4 and type blueman-manager or so but i know it will auto complete it for you. Cheers

---

