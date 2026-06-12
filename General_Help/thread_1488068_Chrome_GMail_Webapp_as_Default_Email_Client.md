---
title: "Chrome GMail Webapp as Default Email Client"
date: 2010-05-19
forum: General Help
---

### Post by megamanexent on 2010-05-19
Many of you probably already know this, but the Gmail web Client can be  set as the default Email client using Prism or Chrome. All you have to  do is create a script file in your home directory and place this into  there. (this is for Chrome by the way)

```
#!/bin/sh

/opt/google/chrome/google-chrome --app="[https://mail.google.com/mail?view](https://mail.google.com/mail?view)=cm&tf=0&to=`echo  $1 | sed 's/mailto://'`"
```Make the script executable, (right click  on file-->Properties-->Permissions-->check box or navigate to  directory and chmod +x the file)

This is great, however, I noticed that when you add that script as the  default mail client, gm-notify insist on bringing you to the compose  message dialog(when gm-notify is set to open the current mail client)  instead of the inbox, so i changed your script to weed that little bug  out!

```
#!/bin/sh
if ($1 > /dev/null); then
/opt/google/chrome/google-chrome  --app="https://mail.google.com/mail/?hl=en&shva=1"
else
/opt/google/chrome/google-chrome  --app="https://mail.google.com/mail?view=cm&tf=0&to=`echo $1 |  sed 's/mailto://'`"
fi
```So now we have the best of both worlds, opening from gm-notify  gives me the inbox, while clicking on an email address gives me the  compose message dialog. 

Thanks to this video for the idea: [http://www.youtube.com/watch?v=WGv9kwwya-w](http://www.youtube.com/watch?v=WGv9kwwya-w)

I hope this helps someone! Also, the script can easily be rewritten for  Firefox.

```
#!/bin/sh
if ($1 > /dev/null); then
firefox "https://mail.google.com/mail/?hl=en&shva=1"
else
firefox "https://mail.google.com/mail?view=cm&tf=0&to=`echo $1 |  sed 's/mailto://'`"
fi
```Here is the code for a prism webapp. You first need to make sure you have Prism installed though apt/synaptic/Software Center. Then Create a web app called "compose mail" without the quotation marks. **Do not** fill in the URL info, just the name of the web app!
```

#!/bin/sh
if ($1 > /dev/null); then
WEBAPP="compose.mail"
TOURL="https://mail.google.com/mail/?hl=en&shva=1"

echo "$TOURL"

echo "[Parameters]
id=compose.mail@prism.app
name=Compose Mail
uri=$TOURL
icon=webapp
status=false
location=false
sidebar=false
navigation=false
trayicon=false" > ~/.webapps/$WEBAPP@prism.app/webapp.ini

"prism" -override "$HOME/.webapps/$WEBAPP@prism.app/override.ini" -webapp $WEBAPP@prism.app

else

#thanks to: http://matthew.ruschmann.net/blog
WEBAPP="compose.mail"

TOMAIL=`echo "${*}" | sed -e 's/mailto://g'`
TOMAIL=`echo "$TOMAIL" | sed -e 's/?/\&/g'`
TOMAIL=`echo "$TOMAIL" | sed -e 's/&subject=/\&su=/g'`

TOURL="https://mail.google.com/mail?view=cm&tf=0&to="

echo "$TOURL${TOMAIL}"

echo "[Parameters]
id=compose.mail@prism.app
name=Compose Mail
uri=$TOURL${TOMAIL}
icon=webapp
status=false
location=false
sidebar=false
navigation=false
trayicon=false" > ~/.webapps/$WEBAPP@prism.app/webapp.ini

"prism" -override "$HOME/.webapps/$WEBAPP@prism.app/override.ini" -webapp $WEBAPP@prism.app

fi
```The script is based on Lightbreeze script which came from this thread [http://ubuntuforums.org/showthread.php?t=912864&page=2](http://ubuntuforums.org/showthread.php?t=912864&page=2) It has been edited to take you to the inbox or a compose message dialogue when appropriate. 
It was [Lightbreeze]("http://ubuntuforums.org/member.php?u=678246") comment and script that greatly helped me. Many Thanks!
 Please give any corrections to the script if needed. Thanks!

---

### Post by K.Mandla on 2010-05-20
Moved to General Help.

---

### Post by kerry_s on 2010-05-20
just install desktop-webmail, select your mail, & set it as your preferred mail client.

---

### Post by elbel86 on 2010-05-31
That's great, but you also mentioned Prism.  I don't see any code for Prism though.  How could that be setup?

---

### Post by megamanexent on 2010-06-01
> **elbel86 said:**
> That's great, but you also mentioned Prism.  I don't see any code for Prism though.  How could that be setup?Pretty much the same way, I updated the first post with Prism info. As I didn't know how to write the script for Prism, I did not include any code the first time. Only difference with Prism is you must create a webapp first. Then continue to place the script as your preferred email client. You might have to sign in to gmail the first time, but after that it should work!

One note is to make sure Prism is installed through synaptic. The Firefox extension of Prism requires you to use your extension within your profile folder. It can be done but requires editing the script to point to the folder. Something like this: 
```
"/usr/lib/firefox-3.6.3/firefox" -app "$HOME/.mozilla/firefox/iny3wcw0.default/extensions/refractor@developer.mozilla.org/prism/application.ini-override "$HOME/.webapps/$WEBAPP@prism.app/override.ini" -webapp $WEBAPP@prism.app"
``` Where iny3wcw0.default is the profile folder. Instead just having 
```
"prism" -override "$HOME/.webapps/$WEBAPP@prism.app/override.ini" -webapp $WEBAPP@prism.app
```

---

