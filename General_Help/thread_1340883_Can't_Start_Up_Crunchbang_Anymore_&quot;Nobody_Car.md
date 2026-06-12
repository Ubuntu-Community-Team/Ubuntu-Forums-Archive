---
title: "Can't Start Up Crunchbang Anymore: &quot;Nobody Cared&quot;"
date: 2009-11-29
forum: General Help
---

### Post by gareim on 2009-11-29
Hi guys, I'm running Crunchbang 9.04, which is based on Ubuntu 9.04 so I thought I could get some help here. When I used Ubuntu 9.04 and Crunchbang 9.04, I had this brightness problem where if a video was started, the brightness goes to 0, and pressing Fn+Up only gave a slightly brighter screen.

I googled for some fixes, and a certain post caught my attention. The post can be found [here]("http://ubuntuforums.org/showthread.php?t=870681&highlight=LENOVO+Y510+BRIGHTNESS&page=21"); it is the first post on that page. I followed the instructions, and rebooted. But when it got to the screen where it said "Boot from (hd0,0) ext3...", it didn't work. Here's what the screen basically looks like.

Starting up...
[ 3.814395] irq 9: nobody cared (try booting with the "irqpoll" option)
[ 3.814610] handlers:
[ 3.814647] [<c02f7d50>] (acpi_irq+0x0/0x23)
[ 3.814752] Disabling IRQ #9

Ironically enough, my brightness problem seems to be fixed. I was able to chagne the brightness when I started a memtest (didn't finish it, because I doubt the problem has anything to do with the mem). Any help would be appreciated! Thanks in advance!

---

### Post by gareim on 2009-11-29
Err... I don't like bumping, but I really don't want to reinstall an OS if I can fix it, and I did post this late at night... so maybe people didn't see? Please help!

---

### Post by phillw on 2009-11-29
> **gareim said:**
> Hi guys, I'm running Crunchbang 9.04, which is based on Ubuntu 9.04 so I thought I could get some help here. When I used Ubuntu 9.04 and Crunchbang 9.04, I had this brightness problem where if a video was started, the brightness goes to 0, and pressing Fn+Up only gave a slightly brighter screen.

I googled for some fixes, and a certain post caught my attention. The post can be found [here]("http://ubuntuforums.org/showthread.php?t=870681&highlight=LENOVO+Y510+BRIGHTNESS&page=21"); it is the first post on that page. I followed the instructions, and rebooted. But when it got to the screen where it said "Boot from (hd0,0) ext3...", it didn't work. Here's what the screen basically looks like.

Starting up...
[ 3.814395] irq 9: nobody cared (try booting with the "irqpoll" option)
[ 3.814610] handlers:
[ 3.814647] [<c02f7d50>] (acpi_irq+0x0/0x23)
[ 3.814752] Disabling IRQ #9

Ironically enough, my brightness problem seems to be fixed. I was able to chagne the brightness when I started a memtest (didn't finish it, because I doubt the problem has anything to do with the mem). Any help would be appreciated! Thanks in advance!

There's no mention of that error mssg in the few pages of posts i read. I guess posting your question there & reading the most recent posts may help you.

Soz I can't be of more assistance.

Phill.

---

