---
title: "Attach sticky notes to desktop"
date: 2010-02-09
forum: General Help
---

### Post by ThomasTheTan on 2010-02-09
Hi,

I'm looking for a way to put an editable todo list on my Ubuntu 9.10 desktop.  It doesn't have to be fancy: in fact, the sticky notes that are already included with Ubuntu are perfect for what I'm looking for.  The only downside to these notes, however, is that they minimize - if other applications are on top of them, the only way to see the note is to minimize all the applications on top or click the sticky note icon twice so that the notes minimize and then come back.

Is there a way to just attach the sticky notes to the desktop, so that I could just hit show desktop and see my todo list?  Another option would be to have some sort of editable text box attached to the panel - when I click on the icon in the panel, the text would appear, and I could type on it then.  When I click on other applications, it minimizes back into the panel.

Does anybody know of any programme out there that could accomplish this?  If so, I would be extremely grateful for your reply.

---

### Post by linux4life88 on 2010-02-09
Do you have Compiz installed by any chance?

If so you can activate the widget layer. If you install Screenlets there will be an option in the program to add the screenlets to a widget layer. The widget layer it will be added to is the widget layer you activated in Compiz. In Compiz you can set a key stroke to view the widget layer. When you hit that key the desktop will dim and it will show what every widget you have, whether, sticky notes, stocks, ect... Really cool and useful. Hope this helps and did not confuse you.

[http://www.screenlets.org/index.php/Home]("http://www.screenlets.org/index.php/Home")

---

### Post by jamesisin on 2010-02-09
Alternatively, you could put a simple text document on your desktop containing your list.  You can then resize the icon large enough to be legible on your desktop.

---

### Post by giovi81 on 2011-01-09
> **linux4life88 said:**
> Do you have Compiz installed by any chance?

If so you can activate the widget layer. If you install Screenlets there will be an option in the program to add the screenlets to a widget layer. The widget layer it will be added to is the widget layer you activated in Compiz. In Compiz you can set a key stroke to view the widget layer. When you hit that key the desktop will dim and it will show what every widget you have, whether, sticky notes, stocks, ect... Really cool and useful. Hope this helps and did not confuse you.

[http://www.screenlets.org/index.php/Home]("http://www.screenlets.org/index.php/Home")

Thank you linux4life88! :D I discovered screenlets and used it to create persistent sticky notes.

I had the same problem of ThomasTheTan (I want sticky notes not to disappear when I click on "show desktop" button)

That's what I did:
1. In terminal type 
        sudo apt-add-repository ppa:screenlets-dev/ppa 
   then
        sudo apt-get update
   and finally
        sudo apt-get install screenlets
2. Go to Application > Accessories > Screenlets
3. In the Screenlets-manager window select the screenlet "Lipik"
(click on it)
4. If you want notes to automatically start on log-in check the checkbox "Auto start on login" (bottom-left side)
5. click "launch/add" (left side)
6. if you do not want notes to stay always above other windows,
right-click on the top of note > Window > uncheck "Keep above"
7. you're done

---

### Post by stallinux on 2011-07-12
Simply ... BRILLIANT!

(me being a fan of low-tech)

> **jamesisin said:**
> Alternatively, you could put a simple text document on your desktop containing your list.  You can then resize the icon large enough to be legible on your desktop.

---

### Post by jamesisin on 2011-07-14
stallinux - Glad you approve.  I read that somewhere, but I don't recall the source.  Tried it and found it too limited for what I do with notes.  Worth remembering though.

---

