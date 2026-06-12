---
title: "Printing via Dlink DIR-320 router"
date: 2010-06-05
forum: General Help
---

### Post by mrmac58 on 2010-06-05
Hi,

As a relative newbie, I have a desktop running Ubuntu 10,  a D-Link DIR 320 router which allows my laptop and desktop to share printers/internet.  I can get my Canon MP250 to print directly from Ubuntu via USB, and it works wireless from laptop, but I don't know how to get it printing via the usb port connected to the router.  Documentation suggests I use  192.168.0.1  but just can't figure out what needs to happen to make the darn thing connect!!  

Can you help please?

---

### Post by vtdesouza on 2010-06-20
****I had the same problem, but solved. What I have manually installed the printer as a network printer. That's a guide (I have a PT-BR Ubuntu, so I'll translate the GUI the best as I can):

1- Go to **System > Administration > Printer**

2- Click to add a new printer

3- Select the option **Network printer > Locate network printer**

4- Insert the IP 192.168.0.1 (router IP address) at the **Network Printer** field them click **Locate**

5- Check if it will appear on the left panel **JetDirect(192.168.0.1)** and if the right port (**9100**) is configured on the right side of the panel

6- Select the right drive for your printer and print a test page

I hope this will be useful for you. Good luck!

---

