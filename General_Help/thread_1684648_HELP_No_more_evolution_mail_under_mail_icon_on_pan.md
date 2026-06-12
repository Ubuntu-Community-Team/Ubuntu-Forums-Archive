---
title: "HELP No more evolution mail under mail icon on panel!!??"
date: 2011-02-09
forum: General Help
---

### Post by test_tube_baby on 2011-02-09
How do I restore evolution mail on my gnome panel icon?
When I click the mail icon there is no evolution mail, there's only an option for chat and broadcast account.

See attached file.

I tried everything from many forums but it just restores my panel to default settings, however, the mail tab doesn't return. please help!

---

### Post by ariandita on 2011-02-25
look like you somehow delte the evolution
you should reinstall evolution mail

---

### Post by howefield on 2011-02-25
Looks like your system wants a restart to complete some updates, when you do, is the problem still there ?

If it is, it might be easier to restore the panels to default, and then put back your customisations.

To reset panels to default...

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

Then

```
killall gnome-panel
```

---

