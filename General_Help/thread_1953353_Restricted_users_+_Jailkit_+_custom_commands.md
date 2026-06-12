---
title: "Restricted users + Jailkit + custom commands"
date: 2012-04-06
forum: General Help
---

### Post by tripialos on 2012-04-06
Here i am again, smashing head for a solution and seeking for knowledge exchange  :-P

So, to the point....

I would like to create a user with restricted access. The main idea is to create a user where:

1) The user will be able to perform specific commands such as ,ping,iptables, tracert,ifconfig BUT with specific parameters.*

2) The user WILL NOT BE ABLE to navigate to root directory or to any other folder except his home directory.

3) The user will be able to connect remotely with ssh.

** Actually I wish to create custom commands for that user in order to be able to view some information but not change any settings. 

For instance i want to create a custom command with the name "firewall" where this command will execute 

"$iptables -L -t nat -xvn"

in this way the user will be able to execute the iptable command to view the forwarding but he wont change the iptable**



I decided to do this job with jailkit. I followed an installation/configuration guide found on ubuntuforum and created a jailed user. All works well, the user can ssh without any problems and has specific commands to execute and most importantly he cannot "touch the OS" since he is jailed.


ISSUES:
1) Now the problem is how do i add my custom commands to the    jailed user?

2) Is there a better solution to do this?

3) I was thinking, what if I don't use any jailkit utility,and i just remove the permission to run the "cd" command from the user. Will this make him unable to navigate to the rest of the system? 

Thanks in advance for any help.

---

