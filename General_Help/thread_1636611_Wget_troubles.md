---
title: "Wget troubles"
date: 2010-12-03
forum: General Help
---

### Post by Woll on 2010-12-03
Hello,

Apologies if this is in the wrong place, or indeed an absolute newbie question.

Though I've been trying to grab files from an Ubuntu Lucid server using wget, which goes well.

However, I'm unable to find how to cause files that already exist not to be re-downloaded, overwritten, or appended. There is about 5GB of files at present, so I'd ideally want a way to just downloaded one's that aren't on the server already; for the sake of bandwidth.

Any help would be really appreciated!

edit: The command I'm using from SSH is wget [ftp://user:login@host/specific/files/here/*.demo4](ftp://user:login@host/specific/files/here/*.demo4)

- Woll (Ubuntu/Linux newbie)

---

### Post by nothingspecial on 2010-12-03
```
wget -nc
```See ```
man wget
```

edit: So ```
wget -nc [ftp://user:login@host/specific/files/here/*.demo4 ]("ftp://user:login@host/specific/files/here/*.demo4")

```

---

### Post by Woll on 2010-12-03
Excellent, thanks!

---

### Post by JL23 on 2010-12-13
sorry to jump into this discussion. I posted my wget query on the Server forum with no luck:

 I am trying to download data from my server using wget.

I send the login details and store the cookie. I then rotate through 50   numbers to copy the data into new files. The saved files are always  blank  i.e 0kb file size.

My website stores data on individual pages e.g.: (i have changed my actual site name to "mywebsite")
[URL="http://admin.mywebsite.com/index.php/print_view/?html=true&order_id=50"]
[/URL]'http://admin.mywebsite.com/index.php/print_view/?html=true&order_id=50

I am trying to rotate through the numbers 50 to 1 and extract the data from each page. 


The code I am using is below:

#!/usr/bin/perl 

system ("wget --post-data   'username=ghssld&password=ewui394&autologin=1' --cookies=on   --keep-session-cookies --save-cookies=cookie.txt   http://admin.mywebsite.com/index.php/login");

$x = 50;
while ($x <= 1) {
    system ("wget --wait=400 --post-data 'html=true&order_id=50'   --referer=http://admin.mywebsite.com/ --cookies=on   --load-cookies=cookie.txt --keep-session-cookies   --save-cookies=cookie.txt   http://admin.mywebsite.com/index.php/print_view/");
    
    system ("wget --post-data 'html=true&order_id=50'   --referer=http://admin.mywebsite.com/ --cookies=on   --load-cookies=cookie.txt --keep-session-cookies   --save-cookies=cookie.txt   http://admin.mywebsite.com/index.php/print_view?");
$x++;
}


Can anyone help me modify my code so data is pulled correctly and the saved files are not blank? 
Thank you

---

