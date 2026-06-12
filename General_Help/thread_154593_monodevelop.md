---
title: "monodevelop"
date: 2006-04-03
forum: General Help
---

### Post by Sweet on 2006-04-03
After installing the version in the repository (v0.7), and having it continually crash, I decided to try the latest stable version (v0.9). So I downloaded the sources and tried to compile them and after a problem with the repository version of gtk-sharp2 being too old I came to a dead end:

```
checking for gtkhtml-sharp-2.0 >= 2.4.0... Requested 'gtkhtml-sharp-2.0 >= 2.4.0' but version of Gtkhtml is 2.3.92
configure: error: Library requirements (gtkhtml-sharp-2.0 >= 2.4.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```

I cannot find a newer version of gtkhtml-sharp anywhere (>=v2.4.0).

Any ideas?

Thanks,

Sweet :-D

---

### Post by Sweet on 2006-04-03
Never mind, I kinda got it sorted, but id still like to know where i can get it from (who is it produced by?).


Thanks,


Sweet

---

### Post by ComplexNumber on 2006-04-03
[quote=Sweet]Never mind, I kinda got it sorted, but id still like to know where i can get it from (who is it produced by?).


Thanks,


Sweet[/quote]
[this]("http://www.mono-project.com/Main_Page") may answer your questions.

---

### Post by adamkane on 2006-04-03
A lot of the latest -sharp stuff requires very up-to-date packages, which are only available in Dapper. Keep searching google for repositories created by third-parties, that provide the missing packages.

It's best to have a second PC, if you are using Breezy and want to have the latest Mono packages. And you might as well make that second PC a Dapper PC as well.

I'm not recommending that you upgrade to Dapper. Dapper is still in development, and a lot of stuff still doesn't work.

---

### Post by Sweet on 2006-04-03
[QUOTE=ComplexNumber][this]("http://www.mono-project.com/Main_Page") may answer your questions.[/QUOTE]

Ive already thoroughly searched the main mono website, and the sources are not there([sources]("http://go-mono.com/sources/")), but thanks anyway.

[QUOTE=adamkane]A lot of the latest -sharp stuff requires very up-to-date packages, which are only available in Dapper. Keep searching google for repositories created by third-parties, that provide the missing packages.

It's best to have a second PC, if you are using Breezy and want to have the latest Mono packages. And you might as well make that second PC a Dapper PC as well.

I'm not recommending that you upgrade to Dapper. Dapper is still in development, and a lot of stuff still doesn't work.[/QUOTE]

Thanks for your reply, its a good idea (i managed to find a 3rd party repo, thats how i managed to solve the problem :) ), i still cant find sources for gtkhtml-sharp2.4.0, but as ive found a precompiled binary i dont need them anymore i guess. I think ill set up a pc with dapper though, like you recommended.

Thanks again, both of you.

Sweet

---

