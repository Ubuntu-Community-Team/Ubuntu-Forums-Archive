---
title: "How To Remove Grub And Install Windows"
date: 2011-08-15
forum: General Help
---

### Post by Static Fallen on 2011-08-15
Sup Ubuntu forums, before I begin I would like to say that I do indeed thoroughly enjoy Linux, especially Ubuntu. and I do intend on coming back to it later on down the road.

Okay, so what I want to do is completely remove Ubuntu and  the Grub Bootloader and install the Windows Bootloader but I am not so sure how to accomplish said task. I bought my laptop with Ubuntu 10.04 installed on it and have since then updated to 11.04. I don't believe windows was previously installed on the laptop but I could be wrong.

I have a Ubuntu 11.04 Live CD, a Windows 7 Ultimate Installation CD, and a Windows 7 Recovery CD.

I have heard that you can remove all the necessary partitions that have Ubuntu/Grub in them through the Ubuntu Installation process but I am not sure which partitions to remove.

Any help would be appreciated and keep in mind that I am not a super computer genius so keep your advice simple and tutorials very specific.

The reason I want to switch over to windows for the time being is because I use a lot of Windows programs very often and Wine just isn't cutting it anymore for some programs :(

Thanks in advance for any support replies :)

---

### Post by Static Fallen on 2011-08-16
Sorry for bumping my thread but I need an answer so I can go to bed because I don not feel like dealing with this to much tomorrow :/

---

### Post by Wim Sturkenboom on 2011-08-16
Just install Windows. It will overwrite the MBR and Grub will be gone. It will also wipe Ubuntu of the HD.

And that you don't want to deal with something tomorrow is not our problem. You should have thought of that yesterday and posted the question yesterday so you would have had the solution today and don't have to wait for tomorrow.

It's plain rude to bump within 24 hours.

---

### Post by Static Fallen on 2011-08-16
> **Wim Sturkenboom said:**
> Just install Windows. It will overwrite the MBR and Grub will be gone. It will also wipe Ubuntu of the HD.

And that you don't want to deal with something tomorrow is not our problem. You should have thought of that yesterday and posted the question yesterday so you would have had the solution today and don't have to wait for tomorrow.

It's plain rude to bump within 24 hours.

My bad, I am not a frequent user of forum sites so I did not know I was being impolite :(

On Topic: I tried just installing Windows 7 but when it prompts me to pick a hard drive it says the partition type isn't  right . Am I supposed to format my whole hard drive or would that muck everything up?

---

### Post by Wim Sturkenboom on 2011-08-16
The thing with forums is that they rely on volunteers. What's urgent for you is not urgent for others ;)

Format your drive. It can't muck anything up, just all your stuff will be gone. So backup if you have anything important.

I suggest that you make 2 partitions; one for windows OS and one for your My Documents.
That way if you ever need to re-install windows you don't loose your data. If you ever see yourself using a dual boot, add a third one (e.g. 20GB).

---

