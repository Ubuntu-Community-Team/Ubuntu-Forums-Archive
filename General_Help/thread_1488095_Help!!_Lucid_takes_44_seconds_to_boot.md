---
title: "Help!! Lucid takes 44 seconds to boot"
date: 2010-05-19
forum: General Help
---

### Post by ComputerJy on 2010-05-19
I've been using lucid since the pre alpha and I don't know why but I think it kept getting slower and slower to me until I've noticed "Windows" for god's sakes starts up faster than lucid!
I've looked for some suggestions but nothing paid off. I've made a boot chart for my boot. I've noticed mount.ntfs-3g is taking too much time but I have no idea how to stop it. My fstab is ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    defaults    0    0
#Entry for /dev/sda5 :
UUID=4f0f20cd-4806-4a3f-90ae-ba4e052f8d15    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda2 :
UUID=F06E1AB96E1A7914    /media/Static    ntfs-3g    defaults,locale=en_US.utf8    00
#Entry for /dev/sda1 :
UUID=AA5660A85660774B    /media/Windows    ntfs-3g defaults,locale=en_US.utf8    00
#Entry for /dev/sda6 :
UUID=b8c84dbb-c552-4b79-91fe-76c41619fb70    none    swap    sw    0    0
/dev/scd0    /media/cdrom0    udf,iso9660    user,noauto,exec,utf8    0    0

```I'm just using the defaults, nothing extra to auto mount
[[IMG]http://img412.imageshack.us/img412/8397/eyadlaptoplucid20100520.png[/IMG]](http://img412.imageshack.us/i/eyadlaptoplucid20100520.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by linuxman94 on 2010-05-19
Can you upload your bootchart to another website (i.e. [Image Shack]("http://imageshack.us/") and link it here?  It is too small to read.

---

### Post by ComputerJy on 2010-05-19
Sorry, I did that before reading your response

---

### Post by ComputerJy on 2010-05-19
I've got it cut back to 32 seconds by fixing the auto mount issue 
The solution was simple. First of all purge and never install the ntfs-config pacakge. Then remove the NTFS partitions from the /etc/fstab file (1 line per partition). Reboot, then delete the old mount points (/media/[PartitionName]) is the default I guess  - You may need root permission to do that. Thats it more than 10 seconds saved:popcorn:

[[IMG]http://img62.imageshack.us/img62/8397/eyadlaptoplucid20100520.png[/IMG]](http://img62.imageshack.us/i/eyadlaptoplucid20100520.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

I'm keeping this thread open for any other suggestions. Because I know I can get it to less than 20 seconds

---

### Post by davidmohammed on 2010-05-19
remove quiet splash during boot and try to observe where the pauses are occurring.  Hopefully that will lead you to what you need to optimize.

---

### Post by ComputerJy on 2010-05-19
Well, bye bye granola. I think I won't be saving the earth for now.
[[IMG]http://img248.imageshack.us/img248/8397/eyadlaptoplucid20100520.png[/IMG]](http://img248.imageshack.us/i/eyadlaptoplucid20100520.png/)

Any other suggestions? Oh and how do I remove some of the TTYs?

---

### Post by WorMzy on 2010-05-19
run 'sudo dpkg-reconfigure console-setup', it'll give you the option to change the number of ttys, change tty font, etc.

---

### Post by ComputerJy on 2010-05-19
> **WorMzy said:**
> run 'sudo dpkg-reconfigure console-setup', it'll give you the option to change the number of ttys, change tty font, etc.
Thanks for the help, I did that and typed in [1-3] instead of 6 but I still get a tty when I press ctrl-alt-F4 ,5,6!

Also for some reason ureadahead decided to ruin my improvements for unknown reasons. I tried rebooting 3 times (and waited 45 seconds so ureadahead can finish off its work) but I still get something like the following from bootchart[[IMG]http://img5.glowfoto.com/images/2010/05/19-1605205479T.png[/IMG]](http://www.glowfoto.com/viewimage.php?img=19-160520L&y=2010&m=05&t=png&rand=5479&srv=img5)[IMG]http://www.glowfoto.com/static_image/19-160520L/5479/png/05/2010/img5/glowfoto[/IMG]

---

### Post by ComputerJy on 2010-05-19
I hate image hosting
[[IMG]http://img208.imageshack.us/img208/8397/eyadlaptoplucid20100520.png[/IMG]](http://img208.imageshack.us/i/eyadlaptoplucid20100520.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

