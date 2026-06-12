---
title: "Can I connect to my university's remote labs in Linux?"
date: 2012-08-16
forum: General Help
---

### Post by juliarain on 2012-08-16
I'm wondering if it is possible to connect to my university's remote labs while using my Linux partition. I would be doing this to use statistical software (SPSS) for a class. 

When I try to connect via the [university website]("http://www.umkc.edu/is/remotelabs/"), I am eventually prompted to download an rdp file, which my computer does not recognize. 

I am currently using Ubuntu 12.04 and Gnome Shell. I do have Windows 7 on another partition; I just normally use my Linux partition because it boots up faster.

---

### Post by jnguyen on 2012-08-16
You can get your school connection info within the .rdp file that you need to download then use that info with your Remote Desktop Client  (RDC) or KRDC.
Hope this will help
jvn

---

### Post by xianbei on 2012-08-16
remmina and rdesktop are really good programs for this application

a quick search will show you how to install and use either.

---

### Post by rukiaEnix on 2012-08-16
As everybody else told you see what info is in that RDP file and use it with a remote terminal client. I always use tsclient.

Just for info RDP is the remote protocol that Windows uses.

---

### Post by juliarain on 2012-08-16
Thanks for your suggestion! I tried it in Remmina and it was unable to connect. I will ask my department's IT guy about this sometime next week to see if I am doing something wrong. When we were talking about a professor's website I was working on, he mentioned I might have to create a secure tunnel to access the server from off-campus, so maybe that's the problem. I have no idea how to go about setting that up.

---

### Post by SeijiSensei on 2012-08-16
Most places use either PPTP or OpenVPN to set up tunnels.  Ask your IT department which they use and if they can help.

In the meantime, I suggest you install a copy of [PSPP]("http://www.gnu.org/software/pspp/"), the open-source clone of SPSS, on your computer and see if you can run the analyses you need with that. You might not need to connect to the university system at all.  PSPP reads and writes SPSS system files in case the data you are using is in that format.  I had to run some survey crosstabs last spring and had no problems using PSPP for tasks like that.  I hadn't used SPSS in a couple of decades, but it all came back.

---

### Post by mizzou_tiger on 2012-11-03
Juliarain I was wondering if you found a solution to the problem. I go to UMKC as well and I am having issues connecting to the vpn on both ubuntu and kubuntu with the instructions that the university gave us linux users. On earlier ubuntu distros I was able to connect but for some reason now I am having issues. Any help would be appreciated!

---

### Post by juliarain on 2012-11-05
No, I never figured it out, and I eventually just gave up. Maybe try contacting the IT people and see if they will meet with you to help? Or try the [KC Linux User Group]("http://www.kclug.org/"). They meet this Wednesday at the downtown library at 6:30. I'm going this week.

---

