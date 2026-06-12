---
title: "Brother MFC-7360N Printer Network Setup"
date: 2011-06-16
forum: General Help
---

### Post by JimBuntu on 2011-06-16
This is what I did to set up a Brother MFC-7360N to print over network connection. (Printer is hardwired to my wifi router). 

AS OF 6/16/2011 there is not a 64bit linux driver. THIS WILL ONLY WORK WITH 32bit! But, it says on the FAQ page that they are currently working on a 64bit driver... 

###PLUG IN YOUR PRINTER VIA USB###

1. Go To [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html") 

2. Click "Printer Driver"

3. Click "MFC-7360N"

4. Download the .deb version of the CUPSWRAPPER and LPR. They should be saved to your "Downloads" folder. 

5. Install LPR Driver with: ```
dpkg  -i  --force-all  (lpr-drivername)
``` Example: "dpkg  -i  --force-all mfc7360nlpr-2.1.0-1.i386.deb"

6. Install CUPS Driver with: ```
 dpkg  -i  --force-all  (cupswrapper-drivername)
``` Example: "dpkg  -i  --force-all cupswrapperMFC7360N-2.0.4-2.i386.deb"

7. Make Sure Everything Went OK: ```
dpkg  -l  |  grep  Brother
```

8a. For USB... open a browser and go to: "http://localhost:631/printers" Then click the "MFC7360N" link. In the first drop down menu there is an option to "Print a Test Page". This should work as it worked for me first time. You may have to change a few things here but it's pretty self explanatory. ***When prompted for a login it's the same as logging into your computer.*** USB PRINTING IS NOW DONE!

8b. For Network... unplug the USB cable. Go to the second drop down menu and select "Modify Printer". Again, when prompted for a login you put the same login as logging into your computer. There you will be able to select the "Current Driver" and click "Modify". After that you should get a message saying "Modification completed successfully". You should now be ready to print. If you go back to the page at "http://localhost:631/printers" you should be able to select "Print Test Page" again and see the magic happen. 

9. DONE. At this point you're all finished and should be able to print wirelessly(laptop) through your network connected printer.

---

### Post by bribabb on 2012-01-10
Just wanted to say thank you for the post.  I was having difficulty finding the right driver/setting combination.  I skipped the USB part (couldn't find a cable) and just changed the device URI to the LPD queue for network printing... worked like a charm.

Thanks again,

Brian

---

### Post by freechelmi on 2012-02-25
Hi thanks For your Tutorial.

before installing brother site drivers , on Ubuntu 11.1O a 7225N is proposed but results in "Not connected" message when trying to print.


Weird that the driver are not integrated in Universe. Maybe they are closed source ? however those brothers should be installed automagically like others I think.

---

### Post by msharmony2001 on 2012-04-26
Thank you so very much.
I now have a working printer.
In Ubuntu 10.04:p

---

### Post by vinay427 on 2012-10-01
When I followed the above steps and omitted the USB part, the online CUPS interface did not display my newly installed driver as one of the options when picking a driver (I used LPD just as bribabb). My solution was to browse for the PPD file which was the only such file in /usr/share/cups/model/ and use that as the driver. It works perfectly now!

---

### Post by JanCeuleers on 2012-10-19
I would just like to say that this page has been helpful to me for getting this printer to work with Ubuntu 12.04 64 bit. So even though the Brother printer drivers have not been updated since February 2011 (which is before the original post above which reported that it works only with 32-bit Ubuntu), I have successfully installed this on my 64-bit machine.

---

