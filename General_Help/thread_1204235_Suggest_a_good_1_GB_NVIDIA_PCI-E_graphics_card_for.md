---
title: "Suggest a good 1 GB NVIDIA PCI-E graphics card for Ubuntu"
date: 2009-07-04
forum: General Help
---

### Post by Stan_1936 on 2009-07-04
A friend is considering Ubuntu and wants to upgrade his ATI Radeon X1400 PCI Express video card.  It is a 3 year old Dell system so I'm presuming that it is PCI-E 1.0.  He has "one PCI-Express X16 slot" and "one PCI-Express X1 slot" available on his system.

Now, I do not have experience with modern systems since mine uses AGP 1.0 so I am quite unfamiliar with the difference between PCI-E X16 and PCI-E X1, so I could not suggest a better card.  His budget is $100(USD), and he wants a 1 GB card, if possible, at that price range.

**[SIZE="5"]Question:[/SIZE]**
What would be a good choice for an NVIDIA card for Ubuntu that meets the above specifications?

NOTE:  He is NOT interested in any other Linux distro and does not play games, but I did show him Compiz.....so running Compiz smoothly is his main priority.

---

### Post by cmost on 2009-07-04
I would heartedly recommend the GeForce 9400 GT! I have this card (the 512 MB version) and find it to be quite efficient for everything I do with Linux.  Of course, I don't play games so I can't speak to gaming performance.  Here's one place to see more:

[http://www.amazon.com/EVGA-01G-P3-N945-LR-GeForce-PCI-E-Graphics/dp/B001EH8FZA](http://www.amazon.com/EVGA-01G-P3-N945-LR-GeForce-PCI-E-Graphics/dp/B001EH8FZA)

These cards can be had quite cheaply at retail outlets like Microcenters and online at tigerdirect.com.  In addition, the latest nvidia drivers work very well with these cards.  I'm using the 180.60 version currently and compiz and screen animation is silky smooth.

---

### Post by Stan_1936 on 2009-07-04
Thanks!  I appreciate the suggestion.  Problem is that your card is **PCI-E 2.0.  I don't think that he has that slot available**, as I mentioned in the first post....or **can it be used anyways**?

Here's a couple of silly questions(I'm sure):
1.  How do you know if the card is DDR2 or if it can support DDR3?  Would you have to look up the specs of the existing card to get this information or is there some other way to know?

2.  I've been unable to find ANYTHING which says NVIDIA GeForce...it's always something like EVGA GeForce?  Is this the same as NVIDIA?

---

### Post by cmost on 2009-07-04
Hi!  The card is backward compatible with PCI-E 1.0 so it will work in the aforementioned system.  The card in question uses DDR2 RAM, but, I believe some manufacturers produce a DDR3 variant.  See here:  [http://www.bit-tech.net/news/industry/2008/09/16/zotac-announces-geforce-9400gt-ddr3-and-geforce-9400gt-ddr3-zone-edition/1](http://www.bit-tech.net/news/industry/2008/09/16/zotac-announces-geforce-9400gt-ddr3-and-geforce-9400gt-ddr3-zone-edition/1)

Which leads me to your last question:  Nvidia doesn't produce cards themselves, rather, they produce the specs and other entities produce the cards.  That's why you see lots of different brands for nvidia cards.  Each manufacturer does things their own way but the end product is indeed the nvidia card.

Enjoy!

---

### Post by ratcheer on 2009-07-04
Funny, I just had to buy a new video card before I recently set up my Ubuntu machine. I got a Sparkle fanless 9400GT card from newegg.com for $40 shipped. I ordered a 512 MB card, but they sent me a 1GB card.

I'm sure it is not a great Windows gamer card, but it is doing a very good job for my Ubuntu machine. For the price, I am very happy. I have loaded the version 185 driver and it is working great!

Tim

---

### Post by ratcheer on 2009-07-04
PS - My machine was new in 2004, so I was also apprehensive about buying a PCI-e v2.0 card. But as I said, it is working, perfectly.

Tim

---

### Post by markharding557 on 2009-07-04
as a dell user myself i can say it is very important to check that your power supply can handle your chosen videocard otherwise you may have to upgrade the power supply

---

### Post by Stan_1936 on 2009-07-04
Can a DDR2 PCI card be used with a system that uses DDR RAM?

> **markharding557 said:**
> as a dell user myself i can say it is very important to check that your power supply can handle your chosen videocard otherwise you may have to upgrade the power supply

How would you go about doing this?  The wattage rating for his system's power supply is 305W.  What would one be looking for on the video card to make the determination as to whether or not it(the card) can be used?

---

### Post by jmfal on 2009-07-04
re:stan
the memory on your video card has nothing to do with your mobo memory,most newer video cards use ddr2/3/4 or 5 because they are faster and take up less space than ddr-1(ddr), a pci-ex1 card will fit intoany pci-e slot,most video cards are pci-ex16 and the x16 slot on mobo is set up for video card
do google on expansion slots  that should explain everything
hope that helps out

---

### Post by Stan_1936 on 2009-07-04
OK, so I finally saw one video card where a power supply rating(power requirement) was given.....but for the others, such as this one, I don't see a power supply rating and I don't see any power cables in the package either:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814127406&Tpk=14-127-406](http://www.newegg.com/Product/Product.aspx?Item=N82E16814127406&Tpk=14-127-406)

> **jmfal said:**
> re:stan
the memory on your video card has nothing to do with your mobo memory,most newer video cards use ddr2/3/4 or 5 because they are faster and take up less space than ddr-1(ddr), a pci-ex1 card will fit intoany pci-e slot,most video cards are pci-ex16 and the x16 slot on mobo is set up for video card
do google on expansion slots  that should explain everything
hope that helps out

Thanks, that helps a lot!

EDIT:  I just found out about the power ratings from the manufacturer's website.  Looks like he is out of luck and will have to settle for the ATI card that came with his system.  His PS wattage simply does not allow for even some 256 MB cards to be used.

---

### Post by cmost on 2009-07-05
New power supplies are insanely cheap.  If you're going to go for the new video card, then do yourself a favor and get a new power supply too.  I've upgraded power supplies in proprietary systems and usually industry standard parts work just fine.

---

### Post by Stan_1936 on 2009-07-05
^^^No can do for right now.  Maybe in the future as he will be using this system for a while.

This is the card he currently has:
[http://reviews.cnet.com/graphics-cards/ati-radeon-x1300-pro/4507-8902_7-31530067.html?tag=mncol;psum](http://reviews.cnet.com/graphics-cards/ati-radeon-x1300-pro/4507-8902_7-31530067.html?tag=mncol;psum)

The system requirements say a 350W power supply is required for this card.  As I mentioned earlier in thsi thread, the Dell system specs say that the system has a 305W power supply!  I don't know how the hell this is even possible, to be quite honest!

Now, we had a quick conversation last evening and pretty much agreed on this card:
[http://www.tigerdirect.com/applications/searchtools/item-Details.asp?EdpNo=4116647&sku=P56-8404&srkey=P56-8404](http://www.tigerdirect.com/applications/searchtools/item-Details.asp?EdpNo=4116647&sku=P56-8404&srkey=P56-8404)

Now, the requirements for that card(scroll down the page) say 300W.

Should this be sufficient wattage?

---

### Post by cmost on 2009-07-05
I would stick with your original plan and do the GeForce 9400 GT; it's simply a better upgrade for the price (only a few dollars more than the GeForce 8 series card you just referenced.)  This card says it requires a minimum 300 watt power supply, which apparently your system has.

Here:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4111744&CatId=3669](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4111744&CatId=3669)

---

### Post by khelben1979 on 2009-07-05
[GeForce 9 Series - Wikipedia]("http://en.wikipedia.org/wiki/GeForce_9_Series") if you need some facts about the different types of cards which comes from this series of cards.

---

