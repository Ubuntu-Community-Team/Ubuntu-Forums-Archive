---
title: "Portable Linux"
date: 2012-05-20
forum: General Help
---

### Post by High Camp on 2012-05-20
Hi All,

This is probably a bit out of place but Ubuntu Forums is probably the best place to get my answer (I actually have 3 questions).

Back story: I'm doing some development for my new employer and much prefer developing in Linux. I often work at home so need something portable to bring back & forth. I've installed dual boot on employers' computers before but would prefer not to so I'm thinking of running Lubuntu from a USB or SD card. Unfortunately I don't see an eSata plug as I think that would be the fastest connection. Finally, it's worth noting my work computer has 8G of RAM and runs Win 7 so any of these options will likely work but I want the most efficient one.

First, what is more efficient, USB or SD card? My understanding is SD cards are more efficient because they're a solid state drive and they're also more durable because of the write process compared to USB. Is that correct?

Second, assuming I use an SD Card, what is more efficient; booting from the SD card or carrying a Virtualbox image on the SD card? I believe when you boot from portable media the entire OS is loaded into RAM whereas Virtualbox simply accesses the .vdi file.

Third & finally, does anyone have any experience with a virtual machine image on an SD card? Is it reasonably fast? Or do I need to be accessing the local hard drive to have a decent operating system?

The final alternative I also considered was setting up remote access to my own Linux box via SSH, RDP, or something. I hate remote access, its never fast enough and you always get that lag.

Any help would be very much appreciated, thanks.

---

### Post by 2F4U on 2012-05-20
It is not per se true that SD cards are faster than usb flash drives. For a comparison look here:

[http://en.wikipedia.org/wiki/Comparison_of_memory_cards](http://en.wikipedia.org/wiki/Comparison_of_memory_cards)

Using a VM introduces an additional layer of complexity and I would say that is slower than starting the OS directly from the drive. So unless you need to have both OS running, i. e. the OS at home and the os on the drive, I would go without VM.

---

### Post by idoitprone on 2012-05-20
> **High Camp said:**
> Hi All,

This is probably a bit out of place but Ubuntu Forums is probably the best place to get my answer (I actually have 3 questions).

Back story: I'm doing some development for my new employer and much prefer developing in Linux. I often work at home so need something portable to bring back & forth. I've installed dual boot on employers' computers before but would prefer not to so I'm thinking of running Lubuntu from a USB or SD card. Unfortunately I don't see an eSata plug as I think that would be the fastest connection. Finally, it's worth noting my work computer has 8G of RAM and runs Win 7 so any of these options will likely work but I want the most efficient one.

First, what is more efficient, USB or SD card? My understanding is SD cards are more efficient because they're a solid state drive and they're also more durable because of the write process compared to USB. Is that correct?

Second, assuming I use an SD Card, what is more efficient; booting from the SD card or carrying a Virtualbox image on the SD card? I believe when you boot from portable media the entire OS is loaded into RAM whereas Virtualbox simply accesses the .vdi file.

Third & finally, does anyone have any experience with a virtual machine image on an SD card? Is it reasonably fast? Or do I need to be accessing the local hard drive to have a decent operating system?

The final alternative I also considered was setting up remote access to my own Linux box via SSH, RDP, or something. I hate remote access, its never fast enough and you always get that lag.

Any help would be very much appreciated, thanks.

[http://distrowatch.com/table.php?distribution=puppy](http://distrowatch.com/table.php?distribution=puppy)

it a good distro on the go
Fast harddrive will only translate speed improvements when you boot or shutdown to save. It loads into ram and can be very snappy
It has wide hardware support with libiraries that can be installed from ubuntu repos

or spends lots of money and go the cotton candy route [http://www.fxitech.com/products/](http://www.fxitech.com/products/)

---

### Post by High Camp on 2012-05-20
Thanks for all the feedback, very much appreciated.

Cotton Candy: I have heard of things like this and have seen a couple other cool projects. I can't wait for the day when we can have screen/keyboard/mouse at work and home and simply carry a HD back & forth. Until then, I'll make some other solution work.

Just looking at usb drives, its funny that these days you can barely buy one <500G but when I was growing up 16G was a big hard drive.

Thanks again,

---

