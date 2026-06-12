---
title: "getting osu! game to run on wine"
date: 2009-10-06
forum: General Help
---

### Post by irishgoth8822 on 2009-10-06
hi, i'm trying to install the game osu! which will, according to this thread:

[http://osu.ppy.sh/forum/viewtopic.php?f=2&t=14614&st=0&sk=t&sd=a&start=0](http://osu.ppy.sh/forum/viewtopic.php?f=2&t=14614&st=0&sk=t&sd=a&start=0)

run with proper configuration of wine. i ran the commands contained in the first post in the thread, and everything installed just fine, but when i try to run the program itself (wine osu.exe--i had to rename the command without the '!' because the terminal wouldnt recognize it and double-clicking on the .exe file didn't do anything) nothing happens, and in terminal i get this:

[email]meghan@meghan-laptop:~/.wine[/email]/drive_c/Program Files/osu!$ wine osu.exe
fixme:actctx:parse_manifest_buffer root element is L"asmv1:assembly", not <assembly>
err:seh:setup_exception_record stack overflow 924 bytes in thread 001b eip 7bc73dd0 esp 00230f94 stack 0x230000-0x231000-0x330000


is there something i can fix, or is this just a no-go?

---

