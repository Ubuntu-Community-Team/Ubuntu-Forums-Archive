---
title: "disable text-smoothing in firefox does not work"
date: 2009-11-25
forum: General Help
---

### Post by kleinenbremer on 2009-11-25
Hi to all Forum users (enough introduction;-) )

I changed to the new ubuntu (used other UbuntuVersions since 1,5 years) and have a problem with firefox text-style: I am not able any longer to disable the text-smoothing. In earlier versions it was possible about the main text options under Ubuntu System Settings.

Now these settings do not have any effect on Firefox...

The option gfx-text-smoothing-ebable under about:config does not work either.... i tryed to set it to diable..but no effect...

Why is text under firefox such a problem with Ubuntu? I also installed OpenSuse and there, the text looks really good under firefox and it is possible to disable textsmoothing with the global system settings...

Thanks a lot for your help and please excuse my English. :-)

---

### Post by kleinenbremer on 2009-11-25
ok, i solved the problem, because I found following Tip in this forum:

create a file fonts.config in home folder

write

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>false</bool>
  </edit>
 </match>
</fontconfig>

and set the setting as you wish...very very poor for Ubuntu. other systems like suse or windows can do it better....

---

