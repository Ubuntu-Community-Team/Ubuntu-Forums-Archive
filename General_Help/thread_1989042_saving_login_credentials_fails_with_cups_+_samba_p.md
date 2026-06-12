---
title: "saving login credentials fails with cups + samba printer"
date: 2012-05-28
forum: General Help
---

### Post by laramichaels1978 on 2012-05-28
I have successfully configured CUPS on Ubuntu 12.04 to connect to a Windows print server. The problem is saving the authentication credentials. 

What I have done:

- System settings -> Printing 
- 'Add'
- Select 'Network Printer', and then at the bottom 'Windows Printer via SAMBA'
- Enter the smb:// URI containing hostname + printer name 


Now, under 'authentication', if I leave the radio button set to "Prompt user if authentication is required" and click 'Verify', then a dialog box pops up, I enter my username and my password leaving "Domain: " set to its default value of "WORKGROUP" and I see a message telling me that "the print share is  accessible". So, it is working!

Now, the problem is that in reality I want this login information to be saved so I choose the radio button "Set authentication details now". I insert the same username and the same password, but clicking the 'Verify' button now produces the message "The print share is inaccessible".

Is this because I am unable to set the domain of the printer to WORKGROUP? How can I have CUPS save this login information?

thank you
~l

---

### Post by jakobb on 2012-08-22
I am experincing the same problem w. 
Ubuntu 12.04 x64
Samba print

If I do not enter my cretidentials, I can print but am promted w. login everytime

If I save the excact same logon info, I cannot print :s

---

