---
title: "Keys not working properly in terminal"
date: 2011-11-05
forum: General Help
---

### Post by rakeshkool27 on 2011-11-05
Hello everyone, I am a new user of ubuntu as well as to this forum, and so I need some help.
Recently I installed Ubuntu 11.10 and its awesome and glossy. The problem is with the terminal. Whenever I try to write some program with vi editor, then the keys such as up,down,right,left arrow keys as well as backspace keys wont work. I mean it does not do the right thing. for example the backspace wont delete any characters,right arrow key will generate letter 'A' and something like that. I have also tried in the profile preferences for the automatic and other options for backspace and delete key, but of no use. 
It would be very kind if you could help me out. Thanks.

---

### Post by hwttdz on 2011-11-05
Also, just noticed you're new, welcome.

vi is a pretty advanced editor, it's quite likely any behavior you're experiencing is by design (in fact h,j,k,l are left,down,up,right in command mode). It's designed to minimize the distance the users fingers need to move to program, i.e. it uses letter keys over arrow keys for movement because it does not require moving the fingers as far.  There are multiple different modes for different types of editing that are usually switched between frequently.  There are single or two key commands for cutting and pasting a line of text.

Nano is probably more similar what you might be accustomed to.  It even has a friendly hit bar at the bottom to tell you that ctrl+o writes (saves) and ctrl+x quits.  I'm not saying you shouldn't use vi (especially if you program loads, and typing speed is the limiting factor in your coding (I find it never is for anyone... unless you're doing it wrong... but that's a different story)), I'm just throwing some options out there.

And if you want to use vi you're going to have to spend some time bonding with the help pages.  And this seems to be a good tutorial: [http://staff.washington.edu/rells/R110/#basics](http://staff.washington.edu/rells/R110/#basics)

---

### Post by haqking on 2011-11-05
everything is covered over at the vi/vim wiki

[http://vim.wikia.com/wiki/Backspace_and_delete_problems](http://vim.wikia.com/wiki/Backspace_and_delete_problems)

[http://vim.wikia.com/wiki/Fix_arrow_keys_that_display_A_B_C_D_on_remote_shell](http://vim.wikia.com/wiki/Fix_arrow_keys_that_display_A_B_C_D_on_remote_shell)

---

### Post by rakeshkool27 on 2011-11-05
Thanks for replying.....the links you provided were infact resourceful but I could not find any helpful solution to it.

---

### Post by rakeshkool27 on 2011-11-08
Although am replying late,finally the problem was resolved by creating a ".vimrc" file and adding the following lines in it...

set showmode
set number
set nocompatible
set syntax=automatic
set backspace=indent,eol,start

Now my vi editor works fine.It feels good to make something ok which was not ok, even if its small problem.
Thanks again HWTTDZ, HAQKING for your so useful resources and help.
There is also a option by using gedit in case the vi doesn't works fine.

---

### Post by haqking on 2011-11-09
> **rakeshkool27 said:**
> Although am replying late,finally the problem was resolved by creating a ".vimrc" file and adding the following lines in it...

set showmode
set number
set nocompatible
set syntax=automatic
set backspace=indent,eol,start

Now my vi editor works fine.It feels good to make something ok which was not ok, even if its small problem.
Thanks again HWTTDZ, HAQKING for your so useful resources and help.
There is also a option by using gedit in case the vi doesn't works fine.

cool, glad you got it sorted.  remember to use the thread tools menu to mark the thread as solved.

Cheers

---

### Post by rakeshkool27 on 2011-11-12
> **haqking said:**
> cool, glad you got it sorted.  remember to use the thread tools menu to mark the thread as solved.

Cheers

Hmmm....just did that....:)

---

