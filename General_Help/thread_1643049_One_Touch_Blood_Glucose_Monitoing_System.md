---
title: "One Touch Blood Glucose Monitoing System"
date: 2010-12-11
forum: General Help
---

### Post by pricetech on 2010-12-11
I know this is niche application, so I don't have high hopes of a solution, but I'm throwing it out there anyway.

My Wife is diabetic and uses the One Touch Ultra Mini to test her blood sugar.  We keep track of it on paper but her new endocrinologist insists we MUST bring the meter at each visit so they can hook it up to their computer and pull the numbers from it.  I want the doctor to have more than just the readings, though I can't force her to look at anything else, because we not only track the readings themselves, but diet, exercise, medications, etc. so I want to pull the readings from the meter myself and add the other relevant information, then submit that to the doctor.

The "kit" includes the cable and windows software.  They do not support anything but windows, not even mac.  In fact, they don't even list Windows 7 as a supported OS, so I don't expect them to begin supporting any other OS any time soon.

I'd like to know if anyone has been able to connect one of these meters to a Linux box and get any data from it.  Raw data is fine as long as it can be determined what's what.

I have XP running in a VM, so I can probably make that work, but I'd really like to be able to use the meter in Ubuntu.

Any help would be greatly appreciated.

---

### Post by Jechem on 2010-12-11
You're best bet would be to just run it in VM or wine. You don't want to mess up interpreting the raw data. The results are important for insulin medication levels. I would not want to have a misplaced number on the result. As a medical practitioner myself I'd say you run it in your VM windows xp. 

These companies have no funding for software programming. They stick to the most user base systems which is windows xp for now.  I've worked in a similar company before and all our instruments run in Windows XP. So, yeah don't expect to have a Ubuntu compatible meter. 

Hope this helped.

---

### Post by chili555 on 2010-12-11
I don't know the exact answer; I've never used the system. I do, however, love a mystery! The first thing I'd try is plug it in! I assume there is a storage device in there somewhere and. if so, Ubuntu might actually mount the storage area just like any USB drive or the media card on a camera. You may be able to open the file(s) and see what kind of file it is. A little Googling may show how to decifer the file. You may get some clues if you open a terminal and do:```
sudo tail -f /var/log/messages
```Plug the device in and watch the terminal and see what messages appear.

You could also try running the software in Wine: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

I also stumbled upon this: [http://www.diabetesforums.com/forum/diabuddies/12411-onetouch-ultrasmart-communication-via.html](http://www.diabetesforums.com/forum/diabuddies/12411-onetouch-ultrasmart-communication-via.html)

It discusses the file format. There may be other discussions at that forum.

Post back and let us know; we'll be glad to help.

---

### Post by cyberphrog on 2010-12-11
If your insurance covers a different type of meter and if your medical provider has the online capability, there are some out there with web-based apps that hold your info and your doctor can access it in real time also.  That's let you access the 'cloud' through any browser.

Otherwise, your thought of running windows in VBox sounds like the best option.  

___________________
Fellow diabetic

---

