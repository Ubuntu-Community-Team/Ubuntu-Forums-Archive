---
title: "Eclipse (Missing java libraries)"
date: 2006-02-16
forum: General Help
---

### Post by Wimm on 2006-02-16
Hi there 

I'm having a problem with my Eclipse installation in Ubuntu Breezy Badger. 
I installed JDK and Eclipse manually. Configured the PATH in 'bash.bashrc' 
I can compile and run classes but the only problem I have is that I can't import libraries. Eclipse doesn't recognize java.awt.*; for example, thus I can't use Forms.
Also when I make a project, save that project and restart Eclipse, I get this error:

[COLOR="Olive"]Unable to create this part due to an internal error. Reason for the failure: The editor class could not be instantiated. This usually indicates that the editor's class name was mistyped in plugin.[/COLOR]

Now what I did next is; 
[LIST]
[*][INDENT]I reïnstalled Ubuntu[/INDENT]
[*][INDENT]installed automatrix from where I installed JRE en JDK[/INDENT]
[*][INDENT]installed Eclipse through apt-get[/INDENT]
[/LIST]
And I get the same errors mentioned above.

Does anyone have a good guide to installing JDK and Eclipse or knows how to solve the problem? 

Greets
Wim

---

### Post by faflu on 2006-05-14
I've got the same message, moreover I can't save any changes to a sourcecode - I receive an error: 'Fail:Null'.
I run Ubuntu 5.1 and Eclipse 3.1 installed through apt-get.

---

