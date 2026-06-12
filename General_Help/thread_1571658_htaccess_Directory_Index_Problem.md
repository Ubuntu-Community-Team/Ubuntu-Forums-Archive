---
title: "htaccess: Directory Index Problem"
date: 2010-09-09
forum: General Help
---

### Post by XMolimoX on 2010-09-09
I'm currently running Ubuntu 10.04 Server and I;ve been running my server for bout a year now (Using 9.04 Previously)

By default, Indexing is disabled in my Apache Config File, But I would like to add it to ONE Folder. So I created the .htaccess file and added this

Options +Indexes

Saved it and Uploaded it to the folder, it worked but only kind off heh.

Now when browsing to this folder I get an "EMPTY" Index instead of a "Error 403 Permission Denied"

So this means the folder does recognize the htaccess file but for some reason it still isn't indexing the files inside the folder.

I Even changed the chmod to all the files to 777 and still no files show up.

(Also if I go directly to the File in the browser, it starts to download, meaning the file is present)

(I Also tried "Options All +Indexes"  since some sites state to use this, but still didn't work)

Any Help would be very very appreciated.

Thanks

Molimo

---

