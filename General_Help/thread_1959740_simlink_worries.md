---
title: "simlink worries"
date: 2012-04-16
forum: General Help
---

### Post by winzip on 2012-04-16
I  have two queries.  When we write this ...

** $ sudo ln -s /usr/local/jboss/bin/jboss_init_ubuntu.sh /etc/init.d/[COLOR=Red]jboss[/COLOR]**

(Q1)[COLOR=Red] jboss  [COLOR=Black]is  created ? 

(Q2) What does ln -s  means ?  
[/COLOR][/COLOR]

---

### Post by mcduck on 2012-04-16
Q1: yes

...and Q2: "ln" for "link", "-s" for "symbolic". :D

---

### Post by winzip on 2012-04-16
> **mcduck said:**
> Q1: yes

...and Q2: "ln" for "link", "-s" for "symbolic". :D

Thanks. That was helpful.

You know there is a next command to this...

*Finally, let&#8217;s add it to the system startup services, so it will run at boot (like Apache and all those kind of services do)*
[B][COLOR=Blue][I]
$ update-rc.d [COLOR=Red]jboss[/COLOR] [COLOR=Black]defaults[/COLOR][/I][/COLOR][/B]


[COLOR=Blue][COLOR=Red][COLOR=Black]I believe its the same [COLOR=Red]**jboss **[/COLOR]we just simlinked in the earlier command. but what is [/COLOR][/COLOR][/COLOR]**[COLOR=Blue]*[COLOR=Black]defaults  ? [/COLOR]*[/COLOR]**[COLOR=Blue][COLOR=Black] I  dont understand this part.[/COLOR][/COLOR][COLOR=Blue][COLOR=Red]
[/COLOR][/COLOR]

---

### Post by mcduck on 2012-04-16
> **winzip said:**
> Thanks. That was helpful.

You know there is a next command to this...

*Finally, let&#8217;s add it to the system startup services, so it will run at boot (like Apache and all those kind of services do)*
[B][COLOR=Blue][I]
$ update-rc.d [COLOR=Red]jboss[/COLOR] [COLOR=Black]defaults[/COLOR][/I][/COLOR][/B]


[COLOR=Blue][COLOR=Red][COLOR=Black]I believe its the same [COLOR=Red]**jboss **[/COLOR]we just simlinked in the earlier command. but what is [/COLOR][/COLOR][/COLOR]**[COLOR=Blue]*[COLOR=Black]defaults  ? [/COLOR]*[/COLOR]**[COLOR=Blue][COLOR=Black] I  dont understand this part.[/COLOR][/COLOR][COLOR=Blue][COLOR=Red]
[/COLOR][/COLOR]
In that command, the "defaults" is just an option given to the *update-rc.d* -command, telling it to add the "jboss" script to the default runlevels. See "man update-rc.d" for more detailed explanation.

---

### Post by winzip on 2012-04-16
> **mcduck said:**
> In that command, the "defaults" is just an option given to the *update-rc.d* -command, telling it to add the "jboss" script to the default runlevels. See "man update-rc.d" for more detailed explanation.

you are very much helpful. I got this part.  thanks for the help.

If I am NOT a root user ,  should not there be a ***sudo ***required in this command ?

something like this ...

[COLOR=Black][B][I]$sudo  update-rc.d jboss defaults

[/I][/B]Can I write this way ?
[/COLOR]

---

### Post by mcduck on 2012-04-16
Sure, you'll need to add the "sudo" to execute that commmand in Ubuntu.

---

### Post by winzip on 2012-04-16
> **mcduck said:**
> Sure, you'll need to add the "sudo" to execute that commmand in Ubuntu.

Thanks

---

