---
title: "PyGTK Call a Button event from an Edit"
date: 2010-05-13
forum: General Help
---

### Post by Patagon on 2010-05-13
Hello,

I have a edit and a button, I need write something in the edit and then press Intro (enter/return) and call the click signal from the button.

I have something of code (I write in the edit and when I press Intro the the button get the focus and then press Intro another time).

[PHP]
    #this is the event click of the button (btningresar)
    def on_btningresar_clicked(self, widget):
        print "something"

    #this is the event key press from the Edit (txtidentifica)
    def on_txtidentifica_key_press_event(self, widget, event):
        if (event.keyval == gtk.keysyms.Return) or (event.keyval == gtk.keysyms.KP_Enter):
            self.glade.get_object("btningresar").grab_focus()
    #I need call the click event from the button (btningresar) (erase the above line)

[/PHP]

Thanks!

---

### Post by blazemore on 2010-05-13
*Bumped for mod read*
Can a mod please move this to Programming Talk?
Thanks

---

### Post by Patagon on 2010-05-14
[PHP]
self.on_btningresar_clicked(self)
[/PHP]

---

