---
title: "A little help integrating a suspend work around"
date: 2010-07-16
forum: General Help
---

### Post by russki_drewski on 2010-07-16
Hi!

I've got an Acer 751h with the infamous gma500 video card which gives all sorts of problems among which is no resuming from suspend. However, [they]("http://ubuntuforums.org/showpost.php?p=9595907&postcount=1438") found a work around for the suspend problem that this computer has:

Remove 'vbetool' via command line or synaptic.
Add 'uswsusp' in the same way.

Run the following command:
    sudo s2ram --force
    *enter password*

What I would like help with is if there is a way to integrate this into Ubuntu instead of having to run this command at the terminal every time I would like to suspend my netbook?

I know there must be something in the system config files where a certain command is run every time someone pushes the suspend button or they select suspend from the shutdown menu. Is there a way to change that command for the one I have here?

This would be so awesome if someone knew how to do it!

Thanks!

---

