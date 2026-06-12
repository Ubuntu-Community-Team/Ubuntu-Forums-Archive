---
title: "How to connect to windows share in Xubuntu?"
date: 2010-03-19
forum: General Help
---

### Post by bilekbp on 2010-03-19
Hello, I have just installed Xubuntu onto my Asus EEE PC netbook, and am confused by a few of the changes between Ubuntu & Xubuntu.

In this case I have a Windows share (technically it is not, but that is how it appears to the network) and I don't know what Xubuntu's equivalent to Ubuntu's Places -> Connect to Server is. Can anyone help me?

Thank you!

---

### Post by bobcollard on 2010-03-19
> **bilekbp said:**
> Hello, I have just installed Xubuntu onto my Asus EEE PC netbook, and am confused by a few of the changes between Ubuntu & Xubuntu.

In this case I have a Windows share (technically it is not, but that is how it appears to the network) and I don't know what Xubuntu's equivalent to Ubuntu's Places -> Connect to Server is. Can anyone help me?

Thank you!
Well, we have places but that particular entry was left out.  If you are connected to the server via wire then it should show up in places.  If it is something you connect to via wifi then you would have to set up the connection through the icon in your task bar.  Right click it and go to Edit Connections.

---

### Post by rbc on 2010-03-19
I may be wrong, but I believe that *Places -> Connect to Server *is a feature of nautilus, or maybe it’s gnome. In either case, not possible with Xubuntu/Xfce, as far as I know, at least not using that method. I tried pyneighborhood, but could never get the correct settings. I had better luck with gigolo though. I ended up instaling the whole gnome desktop on top of Xubuntu so that I could have that Places-> Connect to Server feature

---

### Post by bilekbp on 2010-03-19
> **bobcollard said:**
> Well, we have places but that particular entry was left out.  If you are connected to the server via wire then it should show up in places.  If it is something you connect to via wifi then you would have to set up the connection through the icon in your task bar.  Right click it and go to Edit Connections.
I am sorry, but I don't quite understand. Which icon do you mean?

I am not even seeing a "network" bookmark under Places. I don't mean a wired or wireless network connection, I mean a Windows share that is out on the network that I am trying to connect to, which I would do via Ubuntu/Nautilus by completing the following:

Places -> Connect to Server -> Windows Share -> Share Name

Thanks!

---

### Post by bobcollard on 2010-03-19
> **bilekbp said:**
> I am sorry, but I don't quite understand. Which icon do you mean?

I am not even seeing a "network" bookmark under Places. I don't mean a wired or wireless network connection, I mean a Windows share that is out on the network that I am trying to connect to, which I would do via Ubuntu/Nautilus by completing the following:

Places -> Connect to Server -> Windows Share -> Share Name

Thanks!
You're right, look at the previous post from rbc.  Xubuntu uses Thunar.

---

### Post by bilekbp on 2010-03-19
> **bobcollard said:**
> You're right, look at the previous post from rbc.  Xubuntu uses Thunar.
I have - does this mean that I can't do what I want to do in Xubuntu without installing Gnome stuff? It really has nothing that is equivalent?

---

### Post by bobcollard on 2010-03-19
> **bilekbp said:**
> I have - does this mean that I can't do what I want to do in Xubuntu without installing Gnome stuff? It really has nothing that is equivalent?
Did you look at the Network Icon Menu?  I suggested it in my first reply.

---

### Post by rbc on 2010-03-19
You can get to the Shares on the Ubuntu computer, you just cannot use the Thunar file manager to do it. You need to use other applications like pyneighborhood and gigolo, which are not gnome specific. I simply did not having to use them to browse to the Shares, so I installed gnome desktop environment, which includes the nautilus file manager

---

### Post by bilekbp on 2010-03-19
> **bobcollard said:**
> Did you look at the Network Icon Menu?  I suggested it in my first reply.
I am familiar with this menu, but perhaps (as I stated above) I am confused as to which icon you mean.

I am not trying to connect to a wired or wireless network, I am trying to access a network share. Adding a new wireless connection can't help me, as the network share does not have an SSID and is not actually a wireless connection. So I don't think that can assist me in any way, unless, as I said in my earlier reply to you, I am confused about something...

---

### Post by bobcollard on 2010-03-19
> **bilekbp said:**
> I am familiar with this menu, but perhaps (as I stated above) I am confused as to which icon you mean.

I am not trying to connect to a wired or wireless network, I am trying to access a network share. Adding a new wireless connection can't help me, as the network share does not have an SSID and is not actually a wireless connection. So I don't think that can assist me in any way, unless, as I said in my earlier reply to you, I am confused about something...
What I thought was, it was something you could connect to in the lower right of this screen shot.  Actually I have gigolo too, here, and it shows my two exterior drives and the current partition I'm on of my internal drive.  Perhaps that would connect you to your server?  Gigolo is under System Menu.

---

### Post by bilekbp on 2010-03-20
Thanks, I have found gigolo now, and it appears to give similar functionality, but following the same steps in Xubuntu that I would in Ubuntu does not result in the same success, so I'm not sure what I am doing wrong.

---

### Post by rbc on 2010-03-21
I did not notice this until now……..If I boot into Xubuntu, and use an Xfce session, and try to use Gigolo, the share opens in a nautilus window, not a Thunar window. So I guess if you are getting to the point where you can see the share, but not open it, the cause may be that nautilus is required. Nautilus has a boatload of dependencies, so if installing it is not an option, maybe someone can help you pyneighborhood. This looks like a promising how-to:
[http://idyllictux.wordpress.com/2009/06/05/network-browsing-with-pyneighborhood-in-xubuntu-jaunty/](http://idyllictux.wordpress.com/2009/06/05/network-browsing-with-pyneighborhood-in-xubuntu-jaunty/)

---

