---
title: "Portal Service"
date: 2010-07-29
forum: General Help
---

### Post by Valbowsi on 2010-07-29
[COLOR=black][FONT=Verdana]Hi everyone.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]First of my apologies. This may be the wrong forum for this thread, second i'm a windows admin dipping my toe in the open source world..[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]So here is my first Ubuntu post.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I've been trying to find a solution to the following problems which i think are all linked.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]We are looking to remove our VPN product as a cost saving exercise. It's only used by a handful of staff. I've changed outlook on these PCs to use HTTP over RPC so that’s removed the need for VPN access for email. The next problem is shared drive access. I'm trying to find a solution that allows a web portal for these users to logon to which they can access shared drives from. My first thought was SharePoint but as all of you will be all to aware of it costs a fortune. Next i looked at Alfresco but it seems my idea of trying to setup a link to a shared folder on another file server to look like a document store is off the mark[/FONT][/COLOR]
 
[FONT=Verdana][COLOR=black]The next issue has came up internally. Similar to the above we have a bunch of staff who have a load of shared drives. They want a 'portal like system' which they can logon to and have access to all these shared drive locations with all the documents searchable and even the text within the documents searchable. For example pull me the document called document 1 or all documents with the text product code 141.[/COLOR][/FONT]
 
[COLOR=black][FONT=Verdana]I think both issues can be resolved by the same product or solution. I'm just not sure what that is. Maybe someone out there has had to implement something similar.[/FONT][/COLOR]
 
[FONT=Verdana][COLOR=black]The reason i cant use Alfresco to host the documents is because these files are all part of a windows backup strategy so i need to keep that in place whilst having a link from a browser in a central repository...[/COLOR][/FONT]
 
[COLOR=black][FONT=Verdana]simpless... as the Mearkats say[/FONT][/COLOR]

---

### Post by Zill on 2010-07-29
Valbowsi:  I may be way off base here but [Citadel]("http://www.citadel.org/") (in the repos) *may* be the kind of thing you are looking for, although this will depend on compatibility between your existing "drive-based" structure and the Citadel "room-based" system.

Caveat: I have never used Citadel myself but it looks quite interesting!

---

### Post by Valbowsi on 2010-07-29
Thanks for getting back to me so quick. I've installed this app quickly on a test system and it does look really good. I'm just trying to figure out how to make a "room" show a list of documents on a network share.
I'll RTF abd post back
 
Anyone else have any other ideas?

---

