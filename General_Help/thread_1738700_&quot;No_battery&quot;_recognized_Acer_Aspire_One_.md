---
title: "&quot;No battery&quot; recognized Acer Aspire One 521"
date: 2011-04-25
forum: General Help
---

### Post by ThomasVH on 2011-04-25
Hello all

I'm new to Ubuntu since few months, but it was this week that I decided to finally dual boot it on my netbook alongside W7. (I'm NOT running Ubuntu Netbook Edition)

Everything is working as it should, except the battery status. It says "No battery".
There is a battery, it's a 6-cell Lithium-Ion battery (the orignial that came with my netbook) and it is recognized in Windows without any problem.

My system is an Acer Aspire One 521 with 2GB of DDR3 RAM 1333 and has the AMD Athlon II Neo K125 1.7GHz processor.

I run the latest updates of Ubuntu and these are the things I already tried to fix the problem.

- Unplug the battery and plug it in again while the system was running (cable was connected)
- Update BIOS (was up to date, I checked Acer's website)
- Checked for latest drivers
- Reboot (several times, also in recovery mode)
- Installed docky to check if the battery is displayed there
- In terminal: *sudo acpi -b* but did nothing;
I also tried other commands in terminal that I found in other forums, but none worked ..

Has anyone an idea how to fix this issue? Or someone who got similar problem and solved it?

It's not a critical thing, but it's very handy to know what the battery status is, certainly when at school or when doing important stuff.

All help is much appreciated!

Regards

---

### Post by MoebusNet on 2011-04-25
I'm certainly not an expert on this kind of thing, but I'll offer my 2 cents just in case you aren't offered any better advice.

Does your battery status report correctly in Windows? If not, it may be a BIOS issue rather than a Ubuntu issue.

If you have access to a broadband connection, you can always download different Linux Live-CD images (try [http://distrowatch.com/](http://distrowatch.com/)) to try out on your Acer. Puppy Linux is a small download, for example (< 130 MB). You should be able to tell if your battery status is displayed. You can boot from USB if you don't have a CD drive available (current Ubuntu versions have a tool built-in). The newest Ubuntu version is out in approx. 3 days (Natty Narwhal); you could give it a try as a Live-CD or Live-USB to see if that resolves your issue.

I hope this gives you some ideas for a direction to try out, anyway. Best of luck!

---

### Post by ThomasVH on 2011-04-26
Thanks for the help, MoebusNet!

The battery is recognized in Windows 7 without any problem.

I will first wait for Ubuntu 11.04 to be released and see if my problem is solved.

Until that time, I still hope someone else got some things that I could try so Ubuntu will recognize I've got a battery attached.

And I'll install another Linux based OS to test if that OS will recognize my battery or not.

---

### Post by ThomasVH on 2011-04-27
Update

I installed 11.04 on my system and still no luck .. still the same :(

---

### Post by no_numb on 2011-04-28
Theres a thread here
[http://ubuntuforums.org/showthread.php?t=1558296&page=2](http://ubuntuforums.org/showthread.php?t=1558296&page=2)

and also the russian site with the code on it
[http://glotych.ru/ustanovka-ubuntu-11-04-na-acer-aspire-one-521/](http://glotych.ru/ustanovka-ubuntu-11-04-na-acer-aspire-one-521/) and here [http://glotych.ru/kak-ustanovit-ubuntu-10-10-na-acer-aspire-one-521/](http://glotych.ru/kak-ustanovit-ubuntu-10-10-na-acer-aspire-one-521/)

However I'm a complete noob when it comes to this and I cant get the russian code to work (stuck at second line of code) so if anyone can tell me exactly what I've got to type that would be great.

---

### Post by ThomasVH on 2011-04-28
> **no_numb said:**
>  russian site

Thanks for offering your help, I will use Google translator probably to read the entire article.

Will update if this works or not! :)

---

### Post by no_numb on 2011-04-29
English instructions:
[http://www.question-defense.com/2010/09/26/how-to-recompile-your-ubuntu-10-10-kernel-for-patching-or-to-add-support-for-a-specific-device](http://www.question-defense.com/2010/09/26/how-to-recompile-your-ubuntu-10-10-kernel-for-patching-or-to-add-support-for-a-specific-device)

I'm having issues with it though.


12. Once the kernel is built it will be one directory up in the ~/source file we were originally working in.

1
cd ~/source
2
sudo dpkg -i linux-image-2.6.35.(This part will be whatever name you gave it).deb
3
sudo dpkg -i linux-headers-2.6.35.(This part will be whatever name you gave it).deb

This section its coming up with the file cannot be found. I have updated it as I'm using the 2.6.38 kernel.

Any ideas?

---

### Post by ThomasVH on 2011-04-29
Thanks for the link, I will now re-install Ubuntu.
In the guide, the author used 10.10 and I don't like 11.04 with Unity anyways.

Once I have Ubuntu installed again, I will try to recompile my kernel and I give some feedback as well.

---

### Post by no_numb on 2011-04-29
On the russian site he says he's had the same problems with 11.04 and 10.10 and that to fix it is the same process.

---

### Post by no_numb on 2011-04-30
I cant get it to compile something always goes wrong or it crashes before its finished. Can I compile on my main computer (3ghz x 6 4gb ram etc) then move it over to the netbook and install from there?

What files would I need to copy?

---

### Post by ThomasVH on 2011-04-30
> **no_numb said:**
> Can I compile on my main computer (3ghz x 6 4gb ram etc) then move it over to the netbook and install from there?

What files would I need to copy?

It's certainly not that easy, there should be many files to replace and copy in many different folders .. No way you want to do this manually!

It would be great if a more experienced user could help us out ..

---

### Post by no_numb on 2011-04-30
> **ThomasVH said:**
> It's certainly not that easy, there should be many files to replace and copy in many different folders .. No way you want to do this manually!
 
It would be great if a more experienced user could help us out ..
 
Ah I see. I was hoping I could just patch the kernel then copy it over and install it. Should've known it wouldnt be that easy. Perhaps I just need to wait for my 4gb stick to arrive so the netbook may have a chance of compiling on its own. 
 
It seems to use 80% minimum ram with not much going on. Problem with 1gb of ram with 250mb being used for graphics memory. Always gets stuck before completion and frequently locks up for 5 mins at a time.

---

### Post by ThomasVH on 2011-05-01
> **no_numb said:**
> It seems to use 80% minimum ram with not much going on. Problem with 1gb of ram with 250mb being used for graphics memory. Always gets stuck before completion and frequently locks up for 5 mins at a time.

Had the same issue, so I recently bought 2GB of DDR3 RAM (1330) from Crucial and I see a big increase in overall performance.

So if this battery issue gets fixed, I would be more than happy :P

---

### Post by no_numb on 2011-05-20
Just an update really. 

Once I upgraded the ram the kernel compiled correctly. Just redoing it now due to upgrading to an ssd

---

