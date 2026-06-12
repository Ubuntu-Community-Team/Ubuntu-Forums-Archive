---
title: "the site says:&quot;bookmarkable-user-auth&quot; ,it require username and password.How to do !"
date: 2010-11-29
forum: General Help
---

### Post by Hyvi on 2010-11-29
Hi ,
I encountered a problem : when I open firefox browser , pop up a window as follows :
[COLOR=Red]**"**[/COLOR]a usernmae and password are being requested by [http://localhost:39602]("http://localhost:39602.the") . the site says: "bookmarkable-user-auth"
[IMG]http://hyvi.javaeye.com/upload/picture/pic/77033/59738ba6-075a-3405-915c-af5a67175bcc.png[/IMG]
How to avoid it .

thanks for your help !

---

### Post by Hyvi on 2010-11-29
this is a screenshot :
[IMG]http://ubuntuforums.org/picture.php?albumid=2120&pictureid=7086[/IMG]

---

### Post by miljan on 2010-12-05
I have the same problem... Problem is in Binwood Firefox extension. Go to Tools>Add-ons>Extensions , and disable Binwood

---

### Post by Radio89 on 2010-12-18
Caused by Bindwood extension to enable UbuntuOne sharing bookmarks (maybe linked with proxy settings?).


As [COLOR=Black][Douglas Baigrie]("https://launchpad.net/%7Edbaigrie")[/COLOR] said  [here]("https://answers.launchpad.net/ubuntu/+question/128771") "*To obtain the username and password for  your local couch db (which is where the bookmarks are stored with  Bindwood) execute the following command as your normal user account:*```
awk '/localhost/{split($3, parts, ":"); print "Username: "  substr(parts[2],3); print "Password: " substr(parts[3], 0,  index(parts[3], "@")-1)}' ~/.local/share/desktop-couch/couchdb.html"

```

---

### Post by Eric B on 2010-12-21
Those commands do not work for me. I just opened the file mentioned there to get the username and password.

---

### Post by anuraggautam on 2011-05-30
> **Eric B said:**
> Those commands do not work for me. I just opened the file mentioned there to get the username and password.

Try this, hope this will work for you.

awk '/localhost/{split($3, parts, ":"); print "Username: " substr(parts[2],3); print "Password: " substr(parts[3], 0, index(parts[3], "@")-1)}' ~/.local/share/desktop-couch/couchdb.html

---

### Post by AJH101 on 2011-06-10
This second code works for me, but when I copy and paste the username and password, I am immediately asked for them again?!

Any ideas?

---

