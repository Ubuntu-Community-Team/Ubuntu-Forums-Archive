---
title: "Sony Vaio brightness control on Lucid"
date: 2010-04-30
forum: General Help
---

### Post by progre55_icky on 2010-04-30
Hi people!

After upgrading to Lucid, the brightness control combination (Fn + F5/F6) is not working on my Sony-Vaio VGN-NW21SF.
On Karmic, it was working fine.

Any suggestions, please?

---

### Post by CBung on 2010-04-30
Same problem. The guides seem outdated or too complicated. I had to do it in 9.04, but I recall it was actually as simple as putting 'sony' or something similiar into some config file... Wish I could remember exactly.

---

### Post by Rokyking on 2010-04-30
I know this isn't helping. I am not sure if you guys bug reported it. As it is apparently an issue for a decent amount of people in lucid. If that is what you guys are using. Until then, Wait. 
Breathe Fresh Air 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546201](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546201)


-R

---

### Post by CBung on 2010-04-30
Almost have to go out and breath fresh air because my eyes hurt from it lol

I tried this but it didnt work: [http://vaioubuntu.wordpress.com/2009/05/28/quick-brightness-guide-for-jaunty/](http://vaioubuntu.wordpress.com/2009/05/28/quick-brightness-guide-for-jaunty/)

something about sony-laptop, used to work, guess not now... [email]sadtimes@bung.ca[/email]

---

### Post by Rokyking on 2010-04-30
Are you using the same model as the first poster? Sony-Vaio VGN-NW21SF

If not what model. Seems some have come up with patches for certain specific Vaio Laptops

---

### Post by progre55_icky on 2010-04-30
> **Rokyking said:**
> Seems some have come up with patches for certain specific Vaio Laptops
really? what models? is there a list or smth? and are you sure VGN-NW series are not on the list? :)

damn my eyes hurt..

---

### Post by CBung on 2010-04-30
i am using vgn-fw, but yes if you've heard something let us know :) 

prog, me too :'(

---

### Post by Tucks on 2010-04-30
Add me to the list of Vaio users facing brightness control issues on Lucid. My model is vgn fw 290. The patch mentioned here: [http://vaioubuntu.wordpress.com/2009/05/28/quick-brightness-guide-for-jaunty/](http://vaioubuntu.wordpress.com/2009/05/28/quick-brightness-guide-for-jaunty/) worked under Jaunty ( and Karmic as well on upgrade) but apparently it is not the case when upgraded to Lucid.

Please let  me know your thoughts on this.

K10

---

### Post by danootz on 2010-04-30
VGN-FW here as well. At first at least the brightness indicator appeared when I FN-F5'd it. But now nothing shows up. Even worse I can't seem to manually dim brightness through ubuntu itself. I have to use ATI's catalyst controller (I originally had the flgr or w/e its called installed but no difference)

I really wish these basic functions could be worked out.

---

### Post by panos_m on 2010-05-01
> **danootz said:**
> VGN-FW here as well. At first at least the brightness indicator appeared when I FN-F5'd it. But now nothing shows up. Even worse I can't seem to manually dim brightness through ubuntu itself. I have to use ATI's catalyst controller (I originally had the flgr or w/e its called installed but no difference
I have the same problem with Sony Vaio VGN-FW41E and 10.04. The Fn + F5/F6 buttons worked fine on 9.10. Now I had to uninstall the ATI proprietary drivers and add to the panel the "brightness control applet" as a workaround to quick adjust the brightness.

---

### Post by deathblossom on 2010-05-01
Mine's actually working, I was surprised I didn't have to fiddle with anything like I had to the last three versions.

Sony Vaio VGN-NS240E

---

### Post by jesus225 on 2010-05-02
I have the same problem with a FW31ZJ, I guess all FW laptops are afected. Are the ubuntu guys working in this problem?

---

### Post by St3althcAt on 2010-05-02
Vaio VPCCW1S1E here. Same problem.

---

### Post by CBung on 2010-05-02
I would hope so, but be sure to voice yourself on the bug page: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546201](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546201)

---

### Post by progre55_icky on 2010-05-02
Just posted a comment on the bug report =)

---

### Post by ayden on 2010-05-04
I have the same issue on VPCEA1S1E :(

---

### Post by ed anger on 2010-05-05
I've found the solution:

[http://ubuntuforums.org/showthread.php?p=9242651#post9242651]("http://ubuntuforums.org/showthread.php?p=9242651#post9242651")

---

### Post by progre55_icky on 2010-05-05
> **ed anger said:**
> I've found the solution:

[http://ubuntuforums.org/showthread.php?p=9242651#post9242651](http://ubuntuforums.org/showthread.php?p=9242651#post9242651)

Awesome! It works! thanks man, truly appreciate!

---

### Post by progre55_icky on 2010-05-05
Hmm weird.. it works for kde, but not for gnome..
although I've installed them both on the same machine and not even as dual-boot, but I can choose them on logon. Any suggestions?

---

### Post by ed anger on 2010-05-05
it works for gnome

---

### Post by progre55_icky on 2010-05-05
> **ed anger said:**
> it works for gnome
but strangely, not for my gnome.. not sure what I have done wrong.. and actually, I havent done anything wrong, cause it was fixed for kde..

---

### Post by CBung on 2010-05-05
And if there is no file /etc/default/grub ?

---

### Post by jesus225 on 2010-05-10
This doesn´t work for my fw31zj. The bright still at 100%

---

### Post by jesus225 on 2010-05-19
A fix for my Sony Vaio! (Thank you  Silvan for this solution)
1. Find out the vendor string used by hal:
  $ lshal | grep system.hardware.vendor
  (In my case: system.hardware.vendor = 'Sony Corporation )
 2. Find out the product string:
  $ lshal | grep system.hardware.product
  (In my case: system.hardware.product = 'VGN-FW31ZJ' )
 3. Open /usr/share/hal/fdi/information/10freedesktop/10-laptop-panel-hardware.fdi  in an editor with root privileges
 4. Add this line
 <match key="/org/freedesktop/Hal/devices/computer:system.hardware.vendor"  string="Sony Corporation">
 <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product"  contains_outof="VGN-FW31ZJ">
   <!-- needed since the acpi video module reports it handle the  events, but it don't work on this machines-->
          <merge key="laptop_panel.brightness_in_hardware"  type="bool">false</merge>
        </match>
</match>
5. Reboot!

---

### Post by uvaio on 2010-05-21
not working for me on VGN-SZ4VWN_X ;o(

---

### Post by rmp73 on 2010-05-23
Unfortunately none of the fixes suggested are working for me on a Vaio VGN-FZ11Z either.

---

### Post by Tucks on 2010-06-27
Hi Guys,

I dont know if this issue has been solved or not. If not please tefer to the following site for the resolution:
[http://vaioubuntu.wordpress.com/2010/05/20/lucid-brightness-control-progress/](http://vaioubuntu.wordpress.com/2010/05/20/lucid-brightness-control-progress/)

I upgraded the ati radeon driver from the ati site (version 10.6) 
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

as suggested by a gentleman named "Vanio" and that solved the issue. request you folks to give it a try. Hopefully it should solve the issue.

A big thanks to Vanio for the details posted on the site.

Thanks
ketan

---

### Post by cubabit on 2010-07-24
I can confirm installing the latest ATI drivers (it even allows you to create deb files so hopefully you can upgrade them when it's fixed in the Ubuntu repository) fixed the problem on my Vaio VPCEA1S1E

---

