---
title: "nVidia display problems"
date: 2009-12-12
forum: General Help
---

### Post by oddround on 2009-12-12
I just wanted to share some things I found regarding display problems using Ubuntu 9.04 / 9.10 nVidia 7600GT, nVidia 8600GTS, nVidia 9600GT and 8800GTS.

1.) Display is only  640x480 or 800x600. Some video cables do let you detect the display so display is set to same mode. Bit annoying until you get a different cable.
2.) Grsync data from other machine inherits the display properties you had on the other machine. I found /home/<user name>/.conf a file called monitors.xml . This contains the fix resolution I chose for my old machine. Delete this and display will detect best setting.
Or manually edit this with the resolution you want. "BE CAREFUL!" wrong resolutions can be dangerous. If you are unsure add a second user as administrator and add this user to sudoers and don't mess with this user just use it as a recovery user.
3.) I had trouble with ATI cards so avoided them until now. They used to work better with Kubuntu.
4.) If you backup your user home directory with all your ".*" files it seems to keep all your settings for compiz, mozilla, thunderbird and many more. Handy on a rebuild. Always handy to keep the same user for your rebuild just in case. First user appears to always has the same PID.

Comments welcome.

---

### Post by Raffles10 on 2009-12-12
Funny. I have a Nvidia 8600GTS and have used it wtih Ubuntu 8.04, 8.10, 9.04 & 9.10 without any display problems. My monitor's native 1440x900 is always the default. I would suspect yours is a driver issue. Are you using the proprietary driver ?

---

### Post by oddround on 2009-12-21
This was my first thought but no, I put is a second user and it did not have the problem.
Monitor.xml_old is..,
---------------------
<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="default">
          <vendor>???</vendor>
          <product>0x0000</product>
          <serial>0x00000000</serial>
          <width>1360</width>
          <height>768</height>
          <rate>50</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
      </output>
  </configuration>
</monitors>
-----eof--------------

monitors.xml is..,
---------------------
<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="default">
          <vendor>???</vendor>
          <product>0x0000</product>
          <serial>0x00000000</serial>
          <width>1680</width>
          <height>1050</height>
          <rate>50</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
      </output>
  </configuration>
</monitors>
------eof ----------------

Note resolutions.
The file was inherited from the back where I used Gsync and a "different monitor".
You have a good point though I did not state the driver version. "nVidia 185".

Also (I did not mention again)  the ones where I had 800x600 or 640x480 were old Gforce 2 card (like with 32MBytes ram). The cable was so cheap, one of the thin ones. It now runs 1024x768 on a flat screen 19" monitor with the cube quite happily. Can you believe that! It runs good enough to use.

Sorry about the lack of detail.

---

