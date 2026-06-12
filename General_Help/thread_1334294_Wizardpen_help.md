---
title: "Wizardpen help"
date: 2009-11-22
forum: General Help
---

### Post by drpjkurian on 2009-11-22
Hi guys
I a have been trying to solve my tablet and mousepen for the past one week. Well I appreciate any help to make my tablet work again.

Let me give you the picture of the scenario here.

My machine is Dell Vostro A860 with 2GB RAM and intel dual core chip. It is powered by Ubuntu Karmic with dual desktop display manager.

My tablet is of iball make. My machine recognoised it as UC-LOGIC Tablet WP5540U. I got this output when i entered the command
```
grep -i name /proc/bus/input/devices
```

I was instructed according to help ubuntu tutorial to install Wizardpen driver. I installed the latest driver namely wizardpen-0.7.0-alpha2.tar.gz
I followed the instruction as mentioned in the install file of the Wizardpen driver. 
I also created a new file namely /etc/hal/fdi/policy/99-x11-wizardpen.fdi as mentioned in readme file.

After all this i tried to calibrate but it failed.
Well the present state now after this trial is that my mousepen does not respond at all and the wireless mouse which is supplied along with tablet does not move the cursor but its right and left button works.

Please let me know what shall i do

With regards
Dr Kurian

---

### Post by Favux on 2009-11-22
Hi drpjkurian,

I assume your compile and install of the wizardpen driver went OK without errors?

I think we need to take a look at the .fdi you installed in "/etc/hal/fdi/policy/" and the exact output of:
```
grep -i name /proc/bus/input/devices
```
You might also want to find your tablet in:
```
more /proc/bus/input/devices
```
for more information.

I don't know which HOW TO's you've followed.  Have you seen this [HOW TO]("http://www.jpbouza.com.ar/ESP2/472/genius-tablet-jaunty-and-blender/id/en")?

---

### Post by drpjkurian on 2009-11-23
> **Favux said:**
> Hi drpjkurian,

I assume your compile and install of the wizardpen driver went OK without errors?

I think we need to take a look at the .fdi you installed in "/etc/hal/fdi/policy/" and the exact output of:
```
grep -i name /proc/bus/input/devices
```
You might also want to find your tablet in:
```
more /proc/bus/input/devices
```
for more information.


I don't know which HOW TO's you've followed.  Have you seen this [HOW TO]("http://www.jpbouza.com.ar/ESP2/472/genius-tablet-jaunty-and-blender/id/en")?

Hi Favus

Let me thank you first for responding to my thread.

1.The installation of drivers went without any hassle. To check the integrity of installation, I cheked it with the command```
ls /usr/lib/xorg/modules/input/wizardpen_drv.*
```
The output in the terminal was as follows

/usr/lib/xorg/modules/input/wizardpen_drv.la
/usr/lib/xorg/modules/input/wizardpen_drv.so

So i think it has been installed correctly.


2. The template of my .fdi file looks like this
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP5540U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
                <merge key="input.x11_options.MaxX" type="string">29405</merge>
                <merge key="input.x11_options.MaxY" type="string">29671</merge>
                </match>
            </device>
            </deviceinfo> 

3. the output of the code ```
 grep -i name /proc/bus/input/devices
``` is as follows
N: Name="Lid Switch"
N: Name="Power Button"
N: Name="Sleep Button"
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="UC-LOGIC Tablet WP5540U"
N: Name="Video Bus"
N: Name="Video Bus"
N: Name="PC Speaker"
N: Name="Dell WMI hotkeys"
N: Name="HDA Intel Mic"
N: Name="HDA Intel Mic"
N: Name="HDA Intel Headphone"
N: Name="PS/2 Mouse"
N: Name="AlpsPS/2 ALPS GlidePoint"

4.The output of the code ```
more /proc/bus/input/devices
``` is as follows
I: Bus=0003 Vendor=5543 Product=0004 Version=0100
N: Name="UC-LOGIC Tablet WP5540U"
P: Phys=usb-0000:00:1d.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input5
U: Uniq=
H: Handlers=mouse1 event5 
B: EV=1f
B: KEY=c01 0 3f0001 0 0 0 0 0 0 0 0
B: REL=303
B: ABS=100000f
B: MSC=10

The howto which i have followed is the instruction given in the file namely 'Install' file and the 'Readme' file found in the wizardpen driver folder.

i hope I have answered all your questions satisfactorily. Eagerly awaiting for your response


With regards
Dr Kurian

---

### Post by Favux on 2009-11-23
Hi Dr Kurian,

Thank you, excellent information.

What I would now like to see is the wizardpen.fdi you are currently using and the location you placed it in.

---

### Post by drpjkurian on 2009-11-23
> **Favux said:**
> Hi Dr Kurian,

Thank you, excellent information.

What I would now like to see is the wizardpen.fdi you are currently using and the location you placed it in.

Dear Favus

I presume that I use the .fdi which is placed in 
/etc/hal/fdi/policy

Hope i have answered to the point

With regards
Dr Kurian

---

### Post by Favux on 2009-11-23
Hi drpjkurian,

The problem may be with the wizardpen.fdi you are currently using.  I would like to see it.  Use gedit to view it and copy and paste it in code (#) tags please.  Thank you.

```
gedit /etc/hal/fdi/policy/99-wizardpen.fdi
```
I believe that is the name they recommend using.  Otherwise go to it in Places (Nautilus) and right click on it to view it in Text Editor (gedit).

---

### Post by drpjkurian on 2009-11-23
> **Favux said:**
> Hi drpjkurian,

The problem may be with the wizardpen.fdi you are currently using.  I would like to see it.  Use gedit to view it and copy and paste it in code (#) tags please.  Thank you.

```
gedit /etc/hal/fdi/policy/99-wizardpen.fdi
```
I believe that is the name they recommend using.

Dear Favux
I am hereby attaching the screenshot of my .fdi file. Kindly have a look into it.

With regards
Dr Kurian

---

### Post by drpjkurian on 2009-11-23
Dear Favux

Let me have my dinner. I will catch you later.

With regards
Dr Kurian

---

### Post by drpjkurian on 2009-11-23
> **Favux said:**
> Hi drpjkurian,

The problem may be with the wizardpen.fdi you are currently using.  I would like to see it.  Use gedit to view it and copy and paste it in code (#) tags please.  Thank you.

```
gedit /etc/hal/fdi/policy/99-wizardpen.fdi
```
I believe that is the name they recommend using.  Otherwise go to it in Places (Nautilus) and right click on it to view it in Text Editor (gedit).

Dear Favux

Let me share you an interesting thing. The code ```
gedit /etc/hal/fdi/policy/99-wizardpen.fdi
``` gave me a blank page.

I am hereby attaching the output as a screenshot.
Well the earlier screenshot which i have taken is obtained by navigating to the folder.

Now I strongly think that the problem lies in .fdi

With regards
Dr Kurian

---

### Post by Favux on 2009-11-23
Hi Dr Kurian,

It sure seems like you have done everything right.

The .fdi is called "99-x11-wizardpen.fdi" and it is located in " /etc/hal/fdi/policy/".  The .fdi looks correct:
```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<deviceinfo version="0.2">
  <device>
    <!-- This MUST match with the name of your tablet obtained -->
    <!-- in Step 2 specified previously -->
    <match key="info.product" contains="UC-LOGIC Tablet WP5540U">
      <merge key="input.x11_driver" type="string">wizardpen</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="info.product" type="string">stylus</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

      <!-- Modify these configuration accordingly -->
      <!-- See CONFIGURATION OPTIONS section for the full-set of -->
      <!-- configurable options -->
      <merge key="input.x11_options.TopX" type="string">5619</merge>
      <merge key="input.x11_options.TopY" type="string">6554</merge>
      <merge key="input.x11_options.BottomX" type="string">29405</merge>
      <merge key="input.x11_options.BottomY" type="string">29671</merge>
      <merge key="input.x11_options.MaxX" type="string">29405</merge>
      <merge key="input.x11_options.MaxY" type="string">29671</merge>
    </match>
  </device>
</deviceinfo>
```
Notice that the convention is to indent two spaces for each new device and match line.  This makes it easy to tell that they are "paired".

I added two new lines, which may or may not help.
```
      <merge key="info.product" type="string">stylus</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
```
I suggest rebooting after altering the .fdi.  I would use:
```
gksudo gedit  /etc/hal/fdi/policy/99-x11-wizardpen.fdi   
```
to edit.

Did you calibrate your digitizer?  That is described in the HOW TO I linked you to in the second post.

We may also want to look at your Xorg.0.log to see if a problem is described.  It may also have your coordinate information.  It is located in "/var/log/Xorg.0.log" and you can view it at System > Administration > System Log.

---

### Post by drpjkurian on 2009-11-23
Hi Favux

I am going to bed, I will implement it tomorrow morning

With regards
Dr Kurian

---

### Post by drpjkurian on 2009-11-25
Hi Favux

I have added both lines which you have mentioned in the .fdi file. Now it looks like this. I have attached herewith the edited .fdi. Please have a look into it. Is it ok?

With regards 
Dr Kurian

---

### Post by Favux on 2009-11-25
Hi Dr Kurian,

No that is not what I posted.  Please check again.

You have an extra:
```
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
```
and the stylus line is not in the right place.

By the way using a screenshot like that is not a very useful way to communicate.  Use the code (#) tags on the upper right.

---

### Post by drpjkurian on 2009-11-25
Dear Favux

A Big HUG and THANKS for you my friend. My Tablet, Mousepen as well as wireless mouse is working fine. I am planning to start a HOWTO thread with an acknowledgement as well as credit for you.

Thanking you once again

With regards
Dr Kurian

---

### Post by Favux on 2009-11-25
Hi drpjkurian,

Excellent!  You are welcome.

---

