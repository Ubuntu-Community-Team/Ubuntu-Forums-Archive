---
title: "Printing gets infinite loop of blank pages"
date: 2011-06-25
forum: General Help
---

### Post by TFD on 2011-06-25
I installed Xubuntu and was thrilled to see that it had already setup my Brother HL-2140 USB laser printer. However, there is something seriously wrong with the setup. When you try and print, even a test page - it just churns through the entire paper tray printing nothing.

Also, when you restart the computer it tries to print the jobs again. I went to Printing and selected the printer but could not find where you could see the print job queue. I did see it during troubleshooting and was able to delete the jobs on the troubleshooting screen.

---

### Post by Toz on 2011-06-25
I had the same problem with my HL-2170. I ended up changing the print driver to **PCL 5e - Generic PCL 5e Printer - CUPS+Gutenprint** from the **Generic** class and then it worked fine. 

To view the print queue, select System->Printing, right-click the printer and select "View Print Queue".

---

### Post by TFD on 2011-06-26
> **Toz said:**
> I had the same problem with my HL-2170. I ended up changing the print driver to **PCL 5e - Generic PCL 5e Printer - CUPS+Gutenprint** from the **Generic** class and then it worked fine. 


Thanks for the reply. I selected that generic driver and it didn't loop anymore, but it also didn't print anything, although it made the printer "come alive" for a few seconds. When I was fooling around back in the printer driver dialog it encouraged me to choose Brother and then for the HL-2140 I saw about a half dozen possiblities for my printer. I chose one, and it also would only cause the printer to "come alive" but would not print anything. Then I chose another one and it did print OK! The one I chose is for the HL-2140 but has PCL and 5e in it I believe. The default one that it was recommending had Postscript in it's name and is likely the one that infinitely looped and churned through the paper tray.

---

### Post by wimduk on 2011-07-01
> **TFD said:**
> Thanks for the reply. I selected that generic driver and it didn't loop anymore, but it also didn't print anything, although it made the printer "come alive" for a few seconds. When I was fooling around back in the printer driver dialog it encouraged me to choose Brother and then for the HL-2140 I saw about a half dozen possiblities for my printer. I chose one, and it also would only cause the printer to "come alive" but would not print anything. Then I chose another one and it did print OK! The one I chose is for the HL-2140 but has PCL and 5e in it I believe. The default one that it was recommending had Postscript in it's name and is likely the one that infinitely looped and churned through the paper tray.

Hello there,
I got the same problem with my 2140, followed the procedure, selected the second option in the driver menu  and everthing works fine now. :D Thanks for the help.
wimduk

---

