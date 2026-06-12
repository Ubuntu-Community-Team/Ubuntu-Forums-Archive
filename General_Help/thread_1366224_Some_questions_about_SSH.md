---
title: "Some questions about SSH"
date: 2009-12-28
forum: General Help
---

### Post by Admiral Yi on 2009-12-28
Hello,
I need to us SSh to connect to my laptop from my main PC. In the future, I want to use it the other way round too, but that's not a problem now. I do, however, have a few questions.

_QUESTION 1_
I have SSH all set up (installed server on my laptop), but I'm a little worried about security (im rather paranoid in general ;)). I don't have much knowledge of networks, so bear with me a little.

These are the steps I have taken for security:
1) In hosts.deny I have put 'sshd : all'
2) In hosts.allow I have put 'sshd : 111.111.1.1' (the IP of the one computer I want to connect to the laptop from, obviously that's not my real one)
3) I have also turned root access off

I haven't used security keys because I think passwords should be fine. Are these steps enough to block all access except from my main PC (the ip in hosts allow)? ARe there any other ways to make SSH more secure?


_QUESTION 2_
To connect at the moment, I use 'ssh 222.222.2.2' (the ip of the laptop). Is there a way to get it so I can type 'ssh laptops_name', except using Bash aliases?

_QUESTION 3_
This is where my knowledge of networks falls down. At the moment, both computers are connected to my router with ethernet cables as I don't have wireless. If I were to have my computer connected this way and then my laptop connected up elsewhere (to wireless at a friends house, for example), could I still connect to the laptop in the same way?


Sorry about these questions being really dumb, but as I say I have very little experience using things like SSH before. Any help would be appreciated.

---

### Post by Bachstelze on 2009-12-28
> **Admiral Yi said:**
> 
_QUESTION 1_
I have SSH all set up (installed server on my laptop), but I'm a little worried about security (im rather paranoid in general ;)). I don't have much knowledge of networks, so bear with me a little.

These are the steps I have taken for security:
1) In hosts.deny I have put 'sshd : all'
2) In hosts.allow I have put 'sshd : 111.111.1.1' (the IP of the one computer I want to connect to the laptop from, obviously that's not my real one)
3) I have also turned root access off

I haven't used security keys because I think passwords should be fine. Are these steps enough to block all access except from my main PC (the ip in hosts allow)?

Nope. Here's what [font=monospace]man hosts.allow[/font] says:

> ACCESS CONTROL FILES
       The access control software consults two files. The search stops at the first match:

       ·      Access will be granted when a (daemon,client) pair matches an entry in the /etc/hosts.allow file.

       ·      Otherwise, access will be denied when a (daemon,client) pair matches an entry  in  the /etc/hosts.deny file.

       ·      Otherwise, access will be granted.

       A  non-existing access control file is treated as if it were an empty file. Thus, access control can be turned off by providing no access control files.


Since you have nothing in [font=monospace]hosts.deny[/font] by default, all access will be granted anyway. To achieve what you want, add this to [font=monospace]/etc/hosts.deny[/font]:

```
sshd : *
```

> **Admiral Yi said:**
> ARe there any other ways to make SSH more secure?

What you have done should be enough. Since connections from any other machine will be refused anyway, you don't have to worry about authentication.

> **Admiral Yi said:**
> _QUESTION 2_
To connect at the moment, I use 'ssh 222.222.2.2' (the ip of the laptop). Is there a way to get it so I can type 'ssh laptops_name', except using Bash aliases?

Yes, add a line to your [font=monospace]/etc/hosts[/font] file. Syntax should be pretty straightforward.

> **Admiral Yi said:**
> _QUESTION 3_
This is where my knowledge of networks falls down. At the moment, both computers are connected to my router with ethernet cables as I don't have wireless. If I were to have my computer connected this way and then my laptop connected up elsewhere (to wireless at a friends house, for example), could I still connect to the laptop in the same way?

You would need to have port 22 forwarded on your friend's router (unless it has IPv6, in which case you wouldn't need port forwarding).

---

### Post by Admiral Yi on 2009-12-28
Thanks for the reply. I have made the changes you mentioned. How would I go about forwarding port 22? Would it be possible to do this elsewhere, eg using wireless at an airport (not secure I know, but I can't think of other examples.

---

### Post by Bachstelze on 2009-12-28
> **Admiral Yi said:**
> Thanks for the reply. I have made the changes you mentioned. How would I go about forwarding port 22? Would it be possible to do this elsewhere, eg using wireless at an airport (not secure I know, but I can't think of other examples.

I'm not sure I understand you correctly. Why would you want to have your laptop sitting alone at an airport and connect to it with SSH from somewhere else?

---

### Post by Admiral Yi on 2009-12-28
Ah, sorry, I didn't make that very clear. I mentioned using the laptop to ssh to my computer at the beginning. If I was sitting in an airport with my laptop, what would I need to do to connect to my computer. Equally, if a family member was at the airport with the laptop and had some problems and phoned me to fix them, could I just connect to the laptop with the same command or do I have to do something with the ports?

---

### Post by Bachstelze on 2009-12-28
> **Admiral Yi said:**
> If I was sitting in an airport with my laptop, what would I need to do to connect to my computer.

You would have to have port 22 forwarded on your router at home (or wherever the computer you would want to connect to is). Port forwarding is needed for incoming connections, not for outgoing ones.

> **Admiral Yi said:**
> Equally, if a family member was at the airport with the laptop and had some problems and phoned me to fix them, could I just connect to the laptop with the same command or do I have to do something with the ports?

That would not be possible. Not simply, at least. You would have to create a VPN or something along those lines.

---

### Post by Admiral Yi on 2009-12-28
Ok, thank you. Seeing as you have told me more or less everything I wanted to know, I will mark this solved. Thanks again :).

---

