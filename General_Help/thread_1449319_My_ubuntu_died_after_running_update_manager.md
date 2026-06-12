---
title: "My ubuntu died after running update manager"
date: 2010-04-07
forum: General Help
---

### Post by ebgbnet on 2010-04-07
installed from the 9.1 iso got everything set up all tickety boo.  using it as a local development server.  have been ignoring the update manager, but today for some reason I thought ok, do your thing

fatal

on restarting it gets as far as the splash screen then dies

" * could not access PID file for nmbd"

hit esc to get the grub thing up and tried recovery mode

same deal

so stuck really.

I can hit 'e' and get a basic emacs thing wit a few lines of commands, but not sure what to do there!

I'm not a big terminal user.  I can do stuff I need to and leave it at that.  Do I have to flatten this machine and re-install anything.  Loathe to do that as I spent quite a while getting all the webby bits installed and working as I want to, adn don't really want to have to set all that up again

any ideas?

(falls on knees uttering "I'm not worthy"!)

---

### Post by ebgbnet on 2010-04-08
anybody?

---

### Post by ebgbnet on 2010-04-10
after much searching... I found quite a few threads from folks that have had this happen, but no solution.  Think I found a way around it

the problem is/was when the above error occurred there seemed little way of getting to any sort of shell to investigate further

so, when you get the grub menu, with the option of booting (normal), booting in recovery mode etc...

choose normal and hit return.  as soon s the grub menu disappears and the system is starting to attempt a boot, hit the ESC key.  This seems to interupt the boot process and exit to shell.

timing seems a bit critical so if it doesn't work, control-alt-del and try again

about half a second to a second after making the grub choice seems about right

once in the shell type 

sudo apt-get update

hit return and enter your password.  It re-runs the update process, which appears to write a new version of whatever files were causing it to fail.  let it do its stuff then reboot

grub appears again with a new version available choose that, boot normally and hey ho everything back and tickety boo

well the above has worked for me, so thought it worth sharing in case anyone else comes across this in the future

---

