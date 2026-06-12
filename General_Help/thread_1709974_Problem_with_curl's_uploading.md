---
title: "Problem with curl's uploading"
date: 2011-03-19
forum: General Help
---

### Post by tommmmmm on 2011-03-19
I have a problem with curl. After 3 hours of googling I give up.

The website to upload is:
uploadit.org

the code I use is:
```

  curl -s -A "$USER_AGENT" -o "$session" --cookie "$picHostCookies" --referer "$picHostReferer" --cookie-jar "$cookieJar"  "$picHost"
  #above line just adds session cookies to cookie file
  sleep 1
  #above sleep is just a precausion
  curl -A "$USER_AGENT" -o "$session" --cookie "$cookieJar" --referer "$picHostReferer" -F "$picPostData" -F "$restOfForm" "$picHost"
  #picPostData is userfile1=@/path/to/file/img.jpg
  #restOfForm is friendly1=&folder=Posters-5679&blablabla*&post=post
  #blablabla* are some empty values, that are actually sent when using web browser - I saved page, changed post to get to see what exactly is being sent

```

According to [http://curl.haxx.se/docs/httpscripting.html](http://curl.haxx.se/docs/httpscripting.html)
a button should have a name so I can mimic pressing it (see point 4.3 in the tutorial) however this one doesn't have a name. Probably that's the reason in GET there's post=post at the end.

Curl in verbose mode seems to be uploading a file yet it doesn't get uploaded in the end.

Please I beg for help !


---
edit: I wanted to change topic title to "SOLVED" but I couldn't. I guess only mods can do it

---

### Post by tommmmmm on 2011-03-19
I solved it 2 minutes after posting the thread. As a totally last hope I edited everything into separate forms like this:

```

local restOfForm=' -F friendly1= -F folder1=Posters-5679 -F friendly2= -F folder2= -F friendly3= -F folder3= -F friendly4= -F folder4= -F friendly5= -F folder5= -F post=post'

```
and I added to curl this:
```

curl `echo "$restOfForm"`

```

works now.

Damn wasted 3 hours...

---

