---
title: "Please Help! Dell Wireless Card issue"
date: 2011-09-22
forum: General Help
---

### Post by mlindstrom on 2011-09-22
We use a Dell PowerEdge Windows 2003 Server; half of our users use Laptops, the other half use Desktops. Over the past two months we've been seeing weird issues with our Laptop users.
 
Today we got a better understand of what's happening but not why! Only a handful of users have experienced this issue so far, but the list of people seem to be growing by the day. Here's what we've determined:
 
for example I'll use User "Marc":
 
Marc comes into the office (on a Monday) and connects to our Server/Domain by docking his Dell Latitude E6410 into the Docking Station (using an Ethernet Cable). Marc leaves the office Monday night and heads to Sacramento for an outside the office meeting. Marc then turns his Laptop on Tuesday Morning and connects to a secure Wireless Network (password is/was provided by the Network Admins). Marc is done Tuesday and he turns off his Laptop.
 
Then, Wednesday Marc comes back into the office and connects his Laptop to the Docking Station and turns the Laptop on. The Laptops turns on successfully, Marc logs in, everything seems fine until we notice none of our Networked Mapped Drives re-connect successfully. (which are supposed to be automatically provided to all users through login scripts)
 
At this point- 
 
The user can still access email and the Internet but cannot access any of our Networked Printers, Any of our Networked Drives or Software Programs.
 
The only solution we had found (before today) was to:
 
Login as the User on the Domain (which then has the above problems), leave the domain and join the workgroup (enter server admin password), reboot, login as Admin locally on the Computer, re-join the domain (again entering the server admin password), reboot, and finally login as the User on the domain and everything works fine. All of our Programs work, Network Drives work, etc. Everything is perfect. 
 
Unfortunately the fix is totally roundabout and I don't want to tell this to the users because (A- it's my job to fix it!!! and B- the fix requires the Server Admin password!)
 
Today we determined that it has something to do with the Wireless Card. We found this out because the User came in, logged in and starting having these issues. I asked her if I could sit down and troubleshoot. Before I had troubleshooted by rebooting and nothing was fixed, finally I randomnly decided to leave the domain and re-connect and that worked. SO, today I got crazy (for whatever reason) and decided to disable the wireless card. I disabled the Dell Wireless Card, rebooted the machine and logged in as the User and it worked! OK- now, what's happening with the Wireless Card to block our Networked Drives when the user is using the Ethernet Card!! Please help!! If anyone has any suggestions it would be greatly appreciated! I have been working on this for 48 hours straight, reading Event Logs, other user's notes, troubleshooting basic stuff but my hands are in the air!
 
I currently have 4 user's with Laptops that this happens to. They all use different Dell models (1 uses Latitude D600, D620, D630 & E6400).

---

