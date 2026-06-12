---
title: "Way to make OpenOffice display &quot;Web Layout&quot; by default - or get rid of page gap?"
date: 2011-06-10
forum: General Help
---

### Post by nrundy on 2011-06-10
I always enjoyed the feature in Microsoft Word when in "Print Layout" where I could make the end of one page touch the beginning of the next page so the pages could be viewed seamlessly. There appears to be no way to do this in Writer :(  Anybody know if this is possible in Writer?

As a work around I use WEb Layout to view documents. But everytime I reopen OpenOffice it defaults to Print Layout. Anybody know how to make it default to Web Layout when it is opened?

---

### Post by AlphaLexman on 2011-06-10
This is just a work-around and there may be a better way...

Start OpenOffice Writer -> 'click, View -> Web Layout'

Then save the file as a template as '$HOME/Templates/web_template.ott' (or choose your own filename). Make sure you change the save as filetype to 'ODF Text Document Template (.ott)' in the pull-down box at the bottom right side.

Then from a terminal (or you could create a desktop icon)
```
oowriter ~/Templates/web_template.ott &
```

---

### Post by nrundy on 2011-06-12
Does everyone just view Libreoffice in "Print Layout"?

Is there a way to bring the top and bottom of pages together so no gap exists in Print Layout?

---

### Post by AlphaLexman on 2011-06-13
Did you try my suggestions? They will work for any new documents.

For existing documents, just open the file, click 'View -> Web Layout' and save the file. When you re-open it, it will be in web-layout.

However, I don't think there is a command to open an existing document and **force** a different view other than how the existing document was saved.

---

### Post by nrundy on 2011-06-19
I suppose that's what I'll have to do. But it just seems to me there would be a way to do it without a hack. I appreciate it though.

---

