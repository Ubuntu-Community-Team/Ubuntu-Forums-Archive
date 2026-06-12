---
title: "wget filling forms"
date: 2010-03-24
forum: General Help
---

### Post by bullethead67 on 2010-03-24
I am trying to use wgt to download all the msds files from msds.walmartstores.com 

we buy just about everything from walmart and i have to keep up with the msds files. If I use a space in the product name field it seems to get everything. So I tried using wget to get all the pdf files and I cant get it to work. I have been at this for 4 days. alll i get is the first page no matter what I try. 

here are 4 of MANY things i tried

curl -d txtBoxProName=a -d btmSubmit=Submit [http://msds.walmartstores.com](http://msds.walmartstores.com)

curl --form "txtBoxProName=a&btmSubmit=Submit" [http://msds.walmartstores.com](http://msds.walmartstores.com)

wget --post-data "txtBoxProName=a&btmSubmit=Submit" [http://msds.walmartstores.com](http://msds.walmartstores.com)

wget [http://msds.walmartstores.com/Default.aspx?txtBoxProName=a&btmSubmit=Submit](http://msds.walmartstores.com/Default.aspx?txtBoxProName=a&btmSubmit=Submit)

Can I get a little spoon feeding here. I obviously dont have the ability to figure this out.

---

### Post by doas777 on 2010-03-24
usually the url representation of a space is ```
%20
```

---

### Post by bullethead67 on 2010-03-24
I dont have any spaces. am i supposed to have a space somewhere??

---

### Post by doas777 on 2010-03-24
sorry, i must be confused. i was under the impression you wanted to post a space character to their textbox, so it would return all records. wouldn't be the first time.

---

### Post by bullethead67 on 2010-03-24
Oh im so sorry. youre right. I did try a space though with %20 but it diddnt work. my examples show me trying  to search for the letter a as i was grasping for straws trying to figure it out.

somewhere between me writing the help request and posting the commands I apparently got confused not you. 

how about the commands are they appropriate for form filling or have i left something out?

---

### Post by diesch on 2010-03-24
I usually use *lynx* for this kind of things. Its *-cmd_log* option lets you write all keystrokes to a simple text file,  *-cmd_script* lets you reply them from a file.

---

