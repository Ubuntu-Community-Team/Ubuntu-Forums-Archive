---
title: "Troubleshooting Lua SMTP date???"
date: 2009-08-18
forum: General Help
---

### Post by FuRoSh on 2009-08-18
I've searched and searched with no luck so here I go...
 
I'm a sysadmin and trying to troubleshoot an emailing problem on a ubuntu box. A programmer has been writing Lua scripts and they all seem to work for the most part but I'm trying to troubleshoot an error of emails with Lua being sent with Date: 6/6/6 (all the time) even today on 8-18-09.
 
I have installed and configured exim4 and I have been able to send mail correctly from command line and using:
 
echo "Email Test" | exim4 [EMAIL="email@somedomain.com"]email@somedomain.com[/EMAIL]
 
mail -S "Subject: La La La" [EMAIL="somone@domain.com"]somone@domain.com[/EMAIL]
 
exim4 -d -bt [EMAIL="somone@domain.com"]somone@domain.com[/EMAIL]
 
[FONT=Arial]All these work fine with correct date (8-18-09) being used. I can also debug with the last -d exim 4 command and all looks good![/FONT]

[FONT=Arial]However, anytime I use the Lua script it keeps doing the same thing. Now programmer claims all his stuff is good! :-) Blame game is fun, but I just need to know how to troubleshoot this. The Lua scripts don't seem to use any of the syslogs that get written to for exim4, apache, or anything else.[/FONT]

[FONT=Arial]Does anyone know how to troubleshoot this or what with Lua I can check/verify and fix this issue? Please point me in the right direction....[/FONT]

---

