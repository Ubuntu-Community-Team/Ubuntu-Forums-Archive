---
title: "command line to gui"
date: 2012-01-29
forum: General Help
---

### Post by de Bacon on 2012-01-29
I had a fault happen due to power failure during a program install.  This resulted in a broken OS that doesn't boot up any more.  Sometimes timing is critical in a bad way.  

Running kubuntu 11.04.  
Anyhow my own system understanding (the lack there of) doesn't allow me to fix this, if in fact it can be done.  _What happens._  It starts to boot, though it stops before the OS splash screen kubuntu comes up.  I can see the line commands on the screen as though the entire screen is in terminal.  So, reboot.. and in grub window, I select the item for specific updated kernel's "repair mode" via specific HDD (I think that is what it is called?) where as I selected fix broken packages.  The system runs and again the screen goes to the terminal mode (not in a gui).  It gets to and I go through the login in this terminal equivalent no problem, leaving with command line, but I don't know the command to have the OS switch to the desktop mode of running.  Is there a command to do this.  Back in the old days with windoz 3.1 one could go from the dos shell to windows by typing windows at the prompt.  But this ain't windoz and I have no idea if there is an equivalent command, or what it would be.  From this point, if I reboot again the OS repeats the above, becoming stopped at some point in the start up process.  

The other thing I tried was running the live cd of Kubuntu then using gparted and using the "check" partition option.  No change comes from that, as I have had success with in other errors over the years.  

Any ideas on solution other than a reinstall would be appreciated.  I received some important email that is stuck in this system, so, hopefully I can repair the OS rather than figuring out where and what to retrieve from the HD to retain those evolution files.  

Thanks

---

### Post by BC59 on 2012-01-29
First of all, backup your emails. So boot from a LiveCD (it's the Ubuntu installation CD) and choose Try Ubuntu. Then from the file manager, go to Home and push CTRL+H to see the hidden files. Copy the .evolution folder. Inside are the emails. In a new installation just paste the folder in Home and you'll have all the messages again.
Backup all your personal files as well and the .firefox folder if you like to have the same Firefox settings and bookmarks.

---

### Post by de Bacon on 2012-01-29
> **BC59 said:**
> First of all, backup your emails. 
Yep, I know and do, every week, well almost.  I was not actually aware of any specifics as to how evolution stores its data set.  I use a similar method with firefox, though a little more refined that your suggestion. 

Still this doesn't answer the command line question, or make a statement toward that end my intended hope.  I appreciate your participation and the time to reply.  I have a feeling that if I can get the gui to run one time it will be okay.  

I guess I can and will likely reload during the coming week, and use 11.10 (different HDD) until, sigh.  I am not very fond of 11.10 and prefer 11.04 to it.  

Thanks

---

### Post by de Bacon on 2012-05-01
I enventually did a full reload of the OS,

---

