---
title: "Canon printer. Cant print from network"
date: 2012-08-19
forum: General Help
---

### Post by spiky001 on 2012-08-19
Hi  I,m trying to setup a printer A canon mp190 it is on Ubuntu 10.04 i can run the printer from this PC, but I cant print from laptop (12.04) to the printer on network.  1 question do I have to install drivers on laptop (client) to be able to print.  The CLIENT has got the printer setup in printer setup box but shows the printer with a tick and a (no entry sign) fail  I set the device url to ipp://10.42.43.1/printers/mp190.   I have set the firewall on server to allow tcp port 631.   I think I have covered all

---

### Post by ribongen777 on 2012-08-19
First of all, 

The print, is must you left is on, then and plug to laptop or PC, then search for printing,  to appear, then to see "add" if to recognize your print, then to see if same the model as your print,then click there, that's all there to is.

---

### Post by rickm1945 on 2012-08-19
Click on you Dash( the button that looks like a gear on the upper left hand corner of your desktop), then type print and and you will see printers. Double click on printers. A popup menu will appear and just click add network printer. It will search and should find your printer. 
Make sure your printer is turned on before searching. My laptop didn't find my printer but my printer was turned off on my first try. When I turned the printer on it found it right away.

---

### Post by spiky001 on 2012-08-19
Hi  Ok I rerun the detection of printer and it works I think the problem might have been queued print jobs and the port on the firewall

---

