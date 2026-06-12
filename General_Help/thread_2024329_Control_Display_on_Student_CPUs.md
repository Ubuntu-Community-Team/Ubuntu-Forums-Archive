---
title: "Control Display on Student CPUs"
date: 2012-07-13
forum: General Help
---

### Post by feed5000 on 2012-07-13
Our school's computer lab has 24 student CPUs. We want to be able to use the teacher CPU to take over the students' display as desired (for demonstrations, discipline, etc...). Does anyone have any ideas for this?

I should note: we're all on the same network, but each box is a stand alone Ubuntu installation.

Thanks!

---

### Post by rcayea on 2012-07-13
I believe this should help:

[http://sourceforge.net/projects/italc/](http://sourceforge.net/projects/italc/)

It is called iTALC

---

### Post by feed5000 on 2012-07-13
Alright, iTALC. That looks like what I was looking for! Thanks rcayea. I'll give it a try.

---

### Post by feed5000 on 2012-07-16
I installed & tested iTALC in my lab this morning. So far so good. It does everything I mentioned in my first post. I would recommend it to others. Thank you!

---

### Post by feed5000 on 2012-07-16
I found iTALC poorly documented, and it took me some time to get it working. I found several pages with some instructions, but they were old or incomplete. Here's what worked for me.

iTALC Configuration
How to setup iTALC in a classroom

Phase I: The teacher computer
    -Install iTALC (master)
        --Open Ubuntu Software Center
        --Search for ‘italc-master’
        --Install
    -Restart computer
    -Generate security keys
        --Open Terminal
        --Command: ica -role teacher -createpair
    -Set the key permissions
        --Open Terminal
        --Command: gksudo nautilus (enter password when prompted)
        --Navigate to /etc/italc/keys
        --Private key permissions
            ---Right-click ‘private’ folder
            ---Choose ‘Properties’
            ---Click ‘Permissions’ tab
            ---Set all ‘Folder access’ options to ‘Access files’
            ---Click ‘Apply Permissions to Enclosed Files’
            ---Click ‘Close’.
        --Public key permissions
            ---Right-click ‘public’ folder
            ---Choose ‘Properties’
            ---Click ‘Permissions’ tab
            ---Under Owner, set ‘Folder access’ to ‘Create and delete’
            ---Under Group and Others, set ‘Folder access’ to ‘ Access files’
            ---Click ‘Apply Permissions to Enclosed Files’
            ---Click ‘Close’.
    -Copy keys
        --Open folder /etc/italc/keys
        --Copy folder ‘public’ so that you can move it to other computers

Phase II: The student computers
    -Give the computer a static IP address.
    -Install iTALC (client)
        --Open Ubuntu Software Center
        --Search for ‘italc-client’
        --Install
    -Copy keys from master
        --Open folder /etc/italc/keys
        --Paste folder ‘public’ (that was copied from master computer)

Phase III: Connecting the computers
    -Logon to teacher computer
    -Open iTALC
    -Click the icon on the sidebar that looks like a monitor with magnifying glass.
    -Right click anywhere on the white area that pops-up.
    -Choose ‘Add Computer’
    -Enter the IP address of the client computer
    -Enter some Name for the client computer

---

### Post by rcayea on 2012-07-16
Great information about setting up iTALC in your classroom. Hopefully it helps someone someday. 

Good luck with it.

---

