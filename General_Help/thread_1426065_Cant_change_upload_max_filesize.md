---
title: "Cant change upload_max_filesize"
date: 2010-03-09
forum: General Help
---

### Post by geoffmcc on 2010-03-09
Hello. I have been trying to change the value for "upload_max_filesize" and cant seem to do it,

Anything else i change in php.ini it change takes effect as soon as i restart server, however no matter what i do it will not change "upload_max_filesize"

Can anyone please help, I need to change this and I cant figure out why. Everything i looked at just says to change it in php.ini

---

### Post by geoffmcc on 2010-03-11
anybody have any idea.

---

### Post by alfplayer on 2010-03-11
Is there a semicolon at the beginning of the line *upload_max_filesize ...*? If there is a semicolon, do you what is it for? Do you know you need to remove it to set the new value?

---

### Post by geoffmcc on 2010-03-11
Actually I just now got it to work. I thought I had tried everything. Then it came to me the only other thing I could try was - Before when i was changing the value i deleted the 2 and added 50 saved and restarted server (also i should say i am doing this all from ssh). 

I would check the value with phpinfo and it would always say 2 no matter what. This time, just moments ago rather than delete the value i just added a 5 in front of the default 2 - so it was 52, save restarted apache and it worked.

I don't see why it worked, doesnt seem like anyone else having problems - plus i have done before on prev installs with ease - im not asking questions, as long as it works it works.

---

### Post by alfplayer on 2010-03-11
Were you connecting to the phpinfo web page to check if it changed? Maybe the page was not being reloaded properly.

---

### Post by geoffmcc on 2010-03-12
yea it was being reloaded. I knew what I had said before couldn't really have solved my problem and when i went on to my next step i found what i actually did.

See i was trying to install cchost originally but then gave up and today decided to give a go at geting a podcast host up and running, but that too would require a higher upload value. When I gave up on cchost i restored the original php.ini.

So i installed it and made the changes to php.ini like i said in my previous post and noticed it worked. So now i decided to give cchost another shot.

At a part during the install it shows you your current php.ini settings along with the suggested values. Next to file_uploads it said the value was On and the suggested value was On(1) - I took that as i should change that. Next to max_upload_size it had the correct value rather than showing the default 2M like it has been for days. So i make the change to allow_upload - to say On(1) and as soon as I restarted server the orginal problem was reproduced - max size back to 2M - since i only changed one thing i put it back restarted apache and instantly went back to my value.

It was a case of me taking something too literal. I should have looked at phpinfo seen that uploads were on and not set that value.

---

