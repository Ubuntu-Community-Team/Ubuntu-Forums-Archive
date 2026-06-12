---
title: "sudo echo $USER"
date: 2009-10-09
forum: General Help
---

### Post by whuisonline on 2009-10-09
Hello, everyone. I am VERY confused with the behavior of sudo.
when I type _echo $USER_, the shell shows me _hui_
while trying _sudo echo $USER_, it still give me _hui_ which I thinks, should be _root_

Instead, when I try _env_ and _sudo env_, I get the different outputs.

Any help will be appeciated. Thanks in advance.

---

### Post by Lars Noodén on 2009-10-09
For the full list of what you have set,
```
sudo bash -c set | less
```

$USER is getting parsed before it is sent on to sudo, so

[INDENT][FONT="Courier New"]echo $USER;[/FONT] [/INDENT]
is translated to  
[INDENT][FONT="Courier New"]echo hui[/FONT] [/INDENT]
and then passed on to sudo.  

What will get you the output 'root' would be :

[INDENT][FONT="Courier New"]sudo echo '$USER';[/FONT] [/INDENT]

because the single quotes would make sure that the string gets passed uninterpreted.  This will also respond with the output 'root':

[INDENT][FONT="Courier New"]sudo echo "\$USER";[/FONT][/INDENT]

See the difference between single quotes (**'**) and double quotes (**"**) in bash and 'escape characters'

---

### Post by whuisonline on 2009-10-09
Thanks for your reply. 
I know why I get the same output right now. 
As you indicate, I have tried both *sudo echo '$USER';* and [I][FONT=Courier New]sudo echo "\$USER"; 
[/FONT][/I][FONT=Courier New]But the result is $USER not 'root' :(
Could you make a further explanation ?
[/FONT]

---

### Post by Joeb454 on 2009-10-09
Why not simply run ```
sudo whoami
``` That will provide the result you're looking for.

What that does is essentially the same as ```
echo $user
``` run as root :)

---

### Post by whuisonline on 2009-10-09
Hi jeo. In fact I am not wondering who I am.:P
 I want to figure out the behavior of sudo. 

In addition to my first question, I have another one.

In my ~/.bashrc. I add the following line to declare un environment variable 

```
export FOO=bar
```

In another script called **sudo_bash.sh**, code comes like
```
#!/bin/bash 
echo $FOO
```

When I run sudo_bash.sh by typing ./sudo_bash.sh, it outputs ***bar***.
However, with **sudo ./sudo_bash.sh**, I get nothing.
Furthermore, when I replace **#!/bin/bash** by **#!/bin/bash -i**,
by running with **sudo ./sudo_bash.sh**,  the output ***bar***

It is so confusing.

---

### Post by whuisonline on 2009-10-10
anybody any ideas?

---

