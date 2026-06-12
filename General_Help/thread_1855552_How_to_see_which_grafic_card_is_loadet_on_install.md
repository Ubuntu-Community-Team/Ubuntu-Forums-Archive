---
title: "How to see which grafic card is loadet on install"
date: 2011-10-06
forum: General Help
---

### Post by Mutatos on 2011-10-06
Hi, I have a brand new [HP Desctop PC]("http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c02754767&lang=en&cc=us&taskId=101&contentType=SupportFAQ&prodSeriesId=5035344&prodTypeId=12454")

I have try to install 2 days some distribution of Ubuntu (10.10, 11.04, 11.10 beta 2) and every time the gnome is started after 2-3 minutes of work the ubuntu is freezing. After hard restart it comes the same problem. 

I give the PC to one PC expert, who has installed 5 different linux distributions and ever is coming the same problem. Everytime the linux is started, then it is freezing.

My question is now, is it possible that the onboard grafic card is not disabled right, and it is doing this freezing stuff? HP tells are writing, that "Integrated video is not available if a graphics card is installed" ... but is there a possibility, that this is not the case?

How can I see, which card is loding on ubuntu starting? 

Thanks
Nik

---

### Post by WasMeHere on 2011-10-06
Try the following commands!
```
glxinfo| grep OpenGL
``` and
```
sudo lshw | less
``` and search for 'display' with the interactive command
*/display*.
Post the result to make it easier to help you!

---

