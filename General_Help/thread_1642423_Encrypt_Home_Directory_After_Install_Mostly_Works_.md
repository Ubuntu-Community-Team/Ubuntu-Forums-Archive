---
title: "Encrypt Home Directory After Install Mostly Works But..."
date: 2010-12-10
forum: General Help
---

### Post by ignited on 2010-12-10
Hey Guys,

So when I was initially installing Ubuntu I de-selected the option to have an encrypted home directory (Why is beyond me, and had I known... ). Anyways, a few days later I got the bright idea in my little brain to encrypt my home directory. I looked and found two posts on performing this option. I settled on this post here: [http://ubuntuforums.org/showthread.php?t=1449168](http://ubuntuforums.org/showthread.php?t=1449168)

I followed it mostly... the difference is after I renamed the old user, and created the deleteme account, I created a new user. I again decided (what is with me and these odd decisions?) that I wanted to change the username i was using, and since i was moving everything anyways, why not. So I created the re-named user "nick" into "oldnick". I then created the new user with my new username, we will say "nick-the-idea-man" for the purpose of this post.

Finally I ran*sudo rsync -a /home/oldnick /home/nick-the-idea-man *and this successfully brought over all files from my old directory. 

Now these are my current problems, and I will attempt to explain it the best I can because many things are going on here, and i believe it just boils down to a overblown permissions issue.


[LIST=1]
[*]When the brought the old files over they belonged to the group "nick". (wait what? when did I have a nick group? The post talked about an admin group...)
[*]Certain applications, for example netbeans, when brought over to my "nick-the-idea-man" home directory still retained some old settings. (When I go to connect to a remote server it attempts to put the ssh key in "/home/nick/.sshkeys")
[*]When **update manager** runs, and I attempt to install updates, it asks me for a  password for the user name "oldnick". (remember, user oldnick was just created a few days ago, I installed with username of nick)
[*]Same issue occurs when I attempt to view/alter advanced permissons for users using the "user settings" menu item under System > Administration > Users & Groups
[*]When attempting to remove the user created for this switch ("deleteme"), I get a monumental amount of **"***/usr/sbin/deluser: Cannot handle special file /proc/[insert-every-directory-known-to-man-here]***"** error.
[/LIST]
The one piece of useful information I can offer is what the Authenticate Prompt (for an update manager install or advanced user settings) says:

> 
**You need to authenticate to modify the system configuration**

An application is attempting to perfom an action that requires privileges. Authetication 
as the super user is required to perfom this action.

Password for oldnick: [password box]

> Details
                                  [cancel]  [Authenticate]
---

For anyone wondering these are my theories/solutions.


[LIST=1]
[*]I ran *chown -R nick-the-idea-man.admin folder/* on every folder i copied over to change the group from 'nick' to 'admin'. **please note**: I initially ran this command on the /home/nick-the-idea-man folder and got a ton of "*chown: changing ownership of `nick-the-idea-man/.gvfs/sftp on xxxxxx.com/usr/lib/libsvn_repos-1.la': Function not implemented*" for a ton of stuff in the .gvfs folder. Hence the reason I just changed each one manually.
[*]I think netbeans is a lost cause, I just have to uninstall and do it again. Of course running* ./uninstall.sh* does not work, so I will probably have to manually delete what I can find.
[*]As i'm writing it occured to me that 'oldnick' is the super user (according to that prompt) and perhaps I just need to change the super user.
[/LIST]
Any help anyone and give, even on a part of this issue, would be greatly appreciated!

Thanks,

-Nick

---

