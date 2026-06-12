---
title: "more info on an icon"
date: 2010-07-06
forum: General Help
---

### Post by ignacioguevara on 2010-07-06
Hellou everyone.
I'm new in Ubuntu and I would like some help in changing an icon or in getting more info from an icon
At home I setup a small network between a desktop PC with dual boot (W XP and Ubuntu 9.04), an HP notebook with W Vista (I run Ubuntu 9.10 from a USB key) and my wife's M Vista netbook (untouchabel) all them conected trough a linksys wifi router wired to the internet modem
I notice that in Vista the network icon not only tells me when I'm conected to the internal network (limited conection) but also tells me if I'm conected to the internet by showing a earth globe besides the network item. So if at any moment thart earth globe desapears I know that theres a problem with the internet conection. In Ubuntu there is an icon that shows if there is or not a network connection but I can't see if I have internet connection also. Is there a way that in Ubuntu I can change the network icon so it shows the same info that it shown in Vista?

Thank in advance for your answers

Ignacio

---

### Post by robsoles on 2010-07-07
I haven't come across the functionality that you are asking for in Ubuntu (or other distros I have tried) and I am going to try to explain why (at least why I think it is) as diplomatically as possible.


Microsoft try to make their OS look as functional and superior as possible by hiding all the 'technical' working stuff from all but those willing to spend hours in the arduous task of learning 'all about it' whereas Linux exposes the user to all sorts of technical stuff whilst (hopefully) trying to help them cope.

The 'Linux crowd' know that by trying to get some info from the internet they can quickly determine whether they are connected to it or not and the absolute majority of them realise that if google.com isn't available that doesn't guarantee they are not on the internet - the average Linux user will try three different domains/sites before checking their modem whereas the average Windows user will restart their modem because they can't hit Google!

That's because of the exposure to technicalities as to how what happens on a PC, so to try to make it a little clearer:

My Ex did 2 or 3 years of IT studies, Cert IV in programming and networking, she still contacts me to get her computer back in order when something screws up and plenty of Microsoft updates have put her offline (unable to get any web service whatso-ever) where they Icon you speak of was displaying a little globe and that particular dialog box was saying she was connected.


The software to show you what you want is too easy to produce in any operating system and is probably lurking all over the internet, what the Microsoft one does (my guess to be honest) is checks if a particular process can 'hit' microsoft.com and then leaves it at that, it doesn't check if winsock details and dependencies are all in good order for the user to hit the internet (thus my ex's problems) - good software would check a minimum of three individual locations on the internet was available and only say that system isn't connected to internet if all three were not available.


If you see my point(s) then please mark your thread as resolved, if not then please pose an argument that I or others can discuss.

---

### Post by quinnten83 on 2010-07-07
Nope, there isn't.
So you will just have to ping google or another website.
That we don't have that might not be a bad thing. In order to test that you have network connection, the software in Windows probably pings a website. (perhaps microsoft.com). This to me is too close to dialing home..

---

### Post by robsoles on 2010-07-07
> **quinnten83 said:**
> Nope, there isn't.
So you will just have to ping google or another website.
That we don't have that might not be a bad thing. In order to test that you have network connection, the software in Windows probably pings a website. (perhaps microsoft.com). This to me is too close to dialing home..

I hope I don't offend you quinnten83, just correct me where I am wrong - I want to make sure others can understand what you are saying because I struggled a little to be sure enough to write this...

> Nope, there isn't.He is saying that there is not a lot of software to do this in Linux 'lurking everywhere' on the internet.

> So you will just have to ping google or another website.ping is a command line tool available in a DOS prompt or a CLI/SH/BASH prompt and by using it instead of just putting an address in your browser (or clicking links in for instance an email) you can determine if your browser or something between connectivity and browser is broken!

> That we don't have that might not be a bad thing. In order to test that  you have network connection, the software in Windows probably pings a  website. (perhaps microsoft.com).Yep, we don't want to be 'dumbed down' - not having that 'easy' stuff makes it more sure that we know what is going on!

> This to me is too close to dialing home..So, it's practically dobbing that we run their crap from our IP address - anyone should pick his last line but I thought I would put it another way anyway...

---

### Post by ignacioguevara on 2010-07-07
robsoles and quinnten83 :
Thanks for your answers and expertise. I'm fresh and new at linux so i might be have some bad habits form Microsoft (even when I'm convinced that nothing is so bad or so good in life)
Problem solved
and thanks again

Ignacio

---

