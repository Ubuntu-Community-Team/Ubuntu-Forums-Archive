---
title: "Update Manager error - Solution Needed"
date: 2011-09-22
forum: General Help
---

### Post by Krishna Murthy on 2011-09-22
When I try to update via Update Manager updates are cancelled and the following message is shown.


Not all changes and updates succeeded. For further details of the failure, please expand the ‘Details’ pane below.


apt-listchanges: Mailing root: apt-listchanges: changelogs for krishna-OptiPlex-170L
dpkg: unrecoverable fatal error, aborting:
 syntax error: unknown user 'clamav' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

What does this mean? How do I solve this?

---

### Post by raja.genupula on 2011-09-22
Hi Krishna , do this 
 ```
sudo dpkg-reconfigure -a
```
```
sudo apt-get install -f
```
```
sudo apt-get update
```

and post the output here . 

All the best .

---

### Post by Krishna Murthy on 2011-09-23
> **raja.genupula said:**
> Hi Krishna , do this 
 ```
sudo dpkg-reconfigure -a
```
```
sudo apt-get install -f
```
```
sudo apt-get update
```

and post the output here . 

All the best .

 
Hi Raja

I did exactly as you have mentioned. It comes to this point and stops.


Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring apt-listchanges &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474;  pager        : display changes one page at a time;                         
 &#9474;  browser      : display HTML-formatted changes using a web browser;         
 &#9474;  xterm-pager  : like pager, but in an xterm in the background;              
 &#9474;  xterm-browser: like browser, but in an xterm in the background;            
 &#9474;  gtk          : display changes in a GTK window;                            
 &#9474;  text         : print changes to the terminal (without pausing);            
 &#9474;  mail         : only send changes via e-mail;                               
 &#9474;  none         : do not run automatically from APT.                          
 &#9474;                                                                             
 &#9474;                                                                             
 &#9474; This setting can be overridden at execution time. By default, all the       
 &#9474; options except for 'none' will also send copies by mail.                    
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       
 &#9474;                                                                           &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
 It does not respond here. What is the next step. I rebooted and tried 3 times. The same thing happens everytime.

---

### Post by raja.genupula on 2011-09-23
Hey krishna 
open your terminal & give me the output of ```
sudo apt-get update
```

---

