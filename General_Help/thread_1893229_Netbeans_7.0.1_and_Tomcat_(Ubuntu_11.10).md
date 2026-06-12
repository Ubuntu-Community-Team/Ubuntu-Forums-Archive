---
title: "Netbeans 7.0.1 and Tomcat (Ubuntu 11.10)"
date: 2011-12-09
forum: General Help
---

### Post by peredur on 2011-12-09
I've installed Tomcat6 from the repository[HTML][/HTML] and Netbeans 7 from the netbeans download site.  The netbeans installation is in my home directory.

For some reason, when I tried to install netbeans (6.9) from the repository it didn't show up in the installed software in Dash home or whatever it's called.

Now I'm trying to define Tomcat as a server in netbeans, but I can't get it to recognise /var/lib/tomcat6 as a valid path for CATALINA_HOME in netbeans' Add Server dialog's first page.  I've searched all over and tried the following:

[LIST]
[*]changing the ownership recursively (to my user) on /var/lib/tomcat6 (permissions are 755)
[*]creating a 'private' CATALINA_HOME in my home directory following the instructions at this url [http://stackoverflow.com/questions/3075971/unable-to-add-tomcat-server-instance-in-netbeans-6-9-touch-cannot-touch-usr](http://stackoverflow.com/questions/3075971/unable-to-add-tomcat-server-instance-in-netbeans-6-9-touch-cannot-touch-usr)
[*]using the internal netbeans server, which is configured and starts and stops OK, but doesn't recognise a .war file when I drop it in the webapps folder, and which I can't configure successfully for a manager-gui user despite modifying tomcat-users.xml in exactly the same way as I did for the standalone Tomcat instance.
[/LIST]
None of these works satisfactorily.

Surely this can't be so difficult to do...  So if someone can tell me what I'm completely missing, I'd be very grateful.

I'd be happy to use the repository version of netbeans if it'd help.  Or anything else, for that matter.

Many thanks


Peter

---

### Post by peredur on 2011-12-09
Just discovered that there is no current NetBeans package for Oneiric.

So the question resolves to how do I get Tomcat to work with the downloaded version of Netbeans?

Cheers


Peter

---

### Post by oldtimer7777 on 2011-12-09
Well it won't the way you are doing it. . What I did to get both to install was start clean, with 11.10..  Install the Natty repostiory again temporarily to pull in Netbeans, and install Tomcat just like in 11.04.   Done. 

Remove the Natty repository after you get them both installed and update your Oneiric system. No issues with this work-around.

> **peredur said:**
> Just discovered that there is no current NetBeans package for Oneiric.

So the question resolves to how do I get Tomcat to work with the downloaded version of Netbeans?

Cheer

Peter

---

### Post by peredur on 2011-12-10
Um.  I don't really understand that.  Are you saying that I have to:
[LIST]
[*]Uninstall Tomcat
[*]Add the 11.04 repositories to my repository list
[*]Install Netbeans (from the 11.04 repository)
[*]Reinstall Tomcat
[/LIST]

Do I install Tomcat from the 11.04 repository or from the 11.10 repository?

And why will this make any difference?  How will I define the Tomcat server in Netbeans?  Or will it just allow me to use the Netbeans internal Tomcat server and if so, why would the internal Tomcat server work in this case but not in the case of the downloaded version that I have?

Sorry, but your reply, for me, just raises more questions than it answers.

Thanks for your help and I hope you can put me right on these questions, too.

Cheers


Peter

---

