---
title: "How to edit the shortcuts in nautilus"
date: 2012-05-04
forum: General Help
---

### Post by ukyo_rulz on 2012-05-04
Hello. I would like to know how I can edit the shortcuts that appear at the left side of nautilus (documents, downloads, music, etc). Most of them I want to point to different locations (not in my home folder). Others I want to remove completely. I also want to add additional locations. It seems there is some support for this because if I right-click on a link there is a "remove" option but it is greyed out. I tried to open nautilus with sudo but this just resulted in no shortcuts being displayed at all. Any help would be appreciated.

Edit: I was able to add the locations I wanted by using Bookmarks->Add Bookmark on the menu. All I need now is a way to stop the default bookmarks from being displayed.

Edit: I was finally able to remove the unwanted bookmarks by editing ~/.config/user-dirs.dirs and pointing the unwanted bookmarks to $HOME (commenting them out did nothing)

---

### Post by llamabr on 2012-05-04
Did you try right clicking?  That tends to open all sorts of valuable options.

---

### Post by ukyo_rulz on 2012-05-04
> **llamabr said:**
> Did you try right clicking?  That tends to open all sorts of valuable options.

Like I said, I tried right-clicking the shortcuts but the "remove" option was greyed out.

---

### Post by villalcalde84 on 2012-05-04
To edit the bookmarks, in the menu, go to Bookmarks -> Edit Bookmarks or use the shortcut Ctrl + B; it will open a window with the list of the existing bookmarks. There, you can edit the name, path or even remove them.

Hope this helps.

---

### Post by jerome1232 on 2012-05-04
If you want to make your actual ~/Documents folder point somewhere else, which will make the corresponding bookmark (that's what those things in the left hand pane are) point somewhere else, an easy way is to use symnlinks.

Delete your ~/Documents folder (assuming there's nothing in it of course) then middle click drag the folder you want it to point to to your home folder, rename it to "Documents". Repeat for each folder you want to do this to.

Another way add more bookmarks is to browse to the location and hit ctrl+d.

---

### Post by spiritech on 2012-05-08
none of the above methods work for this.

if you remove them from the bookmarks menu. they do not disappear. if you try editing the .conf/user-dir.dir they disappear then come back on reboot. if you delete the related folders from the home folder then they to just come back on reboot.

please could someone post here if they know how to permanently remove the shortcuts Documents, Downloads, Music, Pictures, Videos and the related Folders from the Home folder.

i know some people might find this feature useful. especially if your the type to constantly accidentally delete folders. but most people dont have this problem.

spiritech

---

### Post by jerome1232 on 2012-05-08
> **spiritech said:**
> none of the above methods work for this.

if you remove them from the bookmarks menu. they do not disappear. if you try editing the .conf/user-dir.dir they disappear then come back on reboot. if you delete the related folders from the home folder then they to just come back on reboot.

please could someone post here if they know how to permanently remove the shortcuts Documents, Downloads, Music, Pictures, Videos and the related Folders from the Home folder.

i know some people might find this feature useful. especially if your the type to constantly accidentally delete folders. but most people dont have this problem.

spiritech

Start a new thread for your separate issue, the op wasn't asking how to remove the shortcuts, the op was asking how to change the location they point to.

---

### Post by spiritech on 2012-05-08
ok.

---

