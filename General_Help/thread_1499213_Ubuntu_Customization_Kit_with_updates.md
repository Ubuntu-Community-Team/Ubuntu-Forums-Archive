---
title: "Ubuntu Customization Kit with updates"
date: 2010-06-01
forum: General Help
---

### Post by csrpazzi on 2010-06-01
Hi I get a couple of months into Linux and Ubuntu (yes I'm a noob on Linux). I'm using 10.04 and y question is: 

When I doing a custom Live CD with UCK, how can I include ubuntu updates with UCK, because after I make a Live USB with the custom ISO it wont include the ubuntu updates and ask me to update when connected to the internet and plugged in (I'm on a laptop).

How can I include also the ubuntu updates when doing the custom ISO? theres an option on the synaptics UCK window to include also the system/ubuntu updates?

Thanks in advance. I hope you can understand.:P

---

### Post by mac9416 on 2010-06-01
Howdy, csrpazzi. Welcome to Ubuntu and UbuntuForums!

I believe that in UCK you can run in the Terminal 'sudo apt-get update' and 'sudo apt-get upgrade' to get the latest updates. However, by the time you install the live CD, there may be more updates. So it may be necessary to re-create the live CD periodically with new updates.

---

### Post by csrpazzi on 2010-06-01
> **mac9416 said:**
> Howdy, csrpazzi. Welcome to Ubuntu and UbuntuForums!

I believe that in UCK you can run in the Terminal 'sudo apt-get update' and 'sudo apt-get upgrade' to get the latest updates. However, by the time you install the live CD, there may be more updates. So it may be necessary to re-create the live CD periodically with new updates.

Thanks and...
I don't think I explain well. What I'm trying to do is create a Custom Live CD with UCK from a ISO image I downloaded from the ubuntu official website and include in that Live CD apps live Inkscape, GIMP, Kdenlive and others, but also I want to include the already released updates for Ubuntu, you know, the updates from the "Update Manager" window. But when creating the Custom Live CD on UCK, UCK give me an option for opening a Synaptics window and choose the software I want to include in the Custom Live CD but I don't see an option to include the updates for ubuntu or something related and on that Synaptics window I don't see neither an option for updates.

And I don't see a solution on your answer
according to me 
"sudo apt-get update" is for update the lists to get software and then download them, is pretty much like the "Reload" button from Synaptics
and "sudo apt-get upgrade" is for upgrade to the latest version of the software.

Well I hope I have explained better than the last time.:P

---

### Post by mac9416 on 2010-06-02
OK, I think I understand now.  :)

If I recall correctly, UCK allows you to enter a live environment on your custom CD. My thought is that, while in this environment, you can open a Terminal and run 'sudo apt-get update && sudo apt-get upgrade'. That will install the latest updates, just like Update Manager would.

Alternatively, I suppose you could simply use Update Manager while in the live environment.

But since we know you can use Synaptic on your live CD, it is probably easiest to upgrade using that. When I open Synaptic, the second large button on the toolbar is "Mark All Upgrades." Do you see that button?

---

### Post by csrpazzi on 2010-06-02
> **mac9416 said:**
> OK, I think I understand now.  :)

If I recall correctly, UCK allows you to enter a live environment on your custom CD. My thought is that, while in this environment, you can open a Terminal and run 'sudo apt-get update && sudo apt-get upgrade'. That will install the latest updates, just like Update Manager would.

Alternatively, I suppose you could simply use Update Manager while in the live environment.

But since we know you can use Synaptic on your live CD, it is probably easiest to upgrade using that. When I open Synaptic, the second large button on the toolbar is "Mark All Upgrades." Do you see that button?

Yes I can see that large button. ](*,)

Maybe if I open the synaptics window from the UCK wizard and choose the "Mark All Upgrades" button you said I can Include the ubuntu updates. I totally miss that button ](*,)

I will post if it worked that tomorrow.

---

