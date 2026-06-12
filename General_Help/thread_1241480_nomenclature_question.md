---
title: "nomenclature question"
date: 2009-08-16
forum: General Help
---

### Post by TooCrooked on 2009-08-16
as a n00b to linux and ubuntu, i am still fairly unfamiliar with the way everything is layered. i have a very broad question about the nomenclature of all things that are layered to create ubuntu..

i just posted a thread about the "alt + print screen" functionality in ubuntu... is that just a package? or is it part of gnome? is gnome a package itself? more specifically, is gnome just a gui package, and nautilus is the explorer package element of gnome that would otherwise work without gnome?

i notice there are pre-installed games with ubuntu... are those separate packages themselves, or are they tied directly to gnome?

a side question... if you run gk- as a prefix to su or sudo, what are you actually invoking? is it something in gnome or something in nautilus?

thanks for any assistance, even if its a link to a changelog or something like that.

---

### Post by dcstar on 2009-08-16
> **TooCrooked said:**
> as a n00b to linux and ubuntu, i am still fairly unfamiliar with the way everything is layered. i have a very broad question about the nomenclature of all things that are layered to create ubuntu..

i just posted a thread about the "alt + print screen" functionality in ubuntu... is that just a package? or is it part of gnome? is gnome a package itself? more specifically, is gnome just a gui package, and nautilus is the explorer package element of gnome that would otherwise work without gnome?

i notice there are pre-installed games with ubuntu... are those separate packages themselves, or are they tied directly to gnome?

a side question... if you run gk- as a prefix to su or sudo, what are you actually invoking? is it something in gnome or something in nautilus?

thanks for any assistance, even if its a link to a changelog or something like that.

The print screen function is a part of whatever graphical desktop you are using, standard Ubuntu uses Gnome, Kubuntu uses KDE etc etc.

Gnome is a collection of packages to provide a functional desktop on top of the X system that Linux uses.

Nautilus is a file browser package that can be used with Gnome.

Some of the games are Gnome games AFAIK.

A "gk" prefix usually indicates a Gnome (graphical) version of a command.

---

### Post by CatKiller on 2009-08-16
> **TooCrooked said:**
>  i just posted a thread about the "alt + print screen" functionality in ubuntu... is that just a package? or is it part of gnome? is gnome a package itself? more specifically, is gnome just a gui package, and nautilus is the explorer package element of gnome that would otherwise work without gnome?

It's a (configurable) keybinding that runs the **gnome-screenshot** command (although you can run a different one instead). gnome-screenshot is provided  by the **gnome-utils** package.

Gnome is a [Desktop Environment]("http://en.wikipedia.org/wiki/Desktop_Environment"), which is constructed from many different elements. Many, many different elements. A lot of those elements can be replaced by something else, and it's possible to mix-and-match a lot of it (window manager, file browser, that kind of thing) but some things have to go together to work properly. It is possible to use Gnome elements (like **nautilus** or **gnome-terminal**) in other desktop environments, and it's possible to use elements of other desktop environments in Gnome.

All software is generally installed as [packages]("http://en.wikipedia.org/wiki/Package_management") in Ubuntu, although it is possible to compile the whole of the Gnome stack (for example) from source if you wanted to. There are some distributions, like Gentoo, that have packages of source code as the install method, and then you compile everything yourself. Some packages contain more than one application, and some packages are meta-packages (like **ubuntu-desktop**) that don't actually include anything themselves - they just depend on all the packages that you need to get whatever function it is that the meta-package is there to provide.

> i notice there are pre-installed games with ubuntu... are those separate packages themselves, or are they tied directly to gnome?A bit of both. They are separate packages that are included with the default Gnome installation. You can remove them if you wish and the rest of Gnome will continue to function, or you can install the default games from another desktop environment (that may not look as well-integrated) quite happily.

> a side question... if you run gk- as a prefix to su or sudo, what are you actually invoking? is it something in gnome or something in nautilus?You're running a different application. **gksudo** is not the same program as **sudo** or **kdesu**. It uses the same backend functions, but the interface is different. It creates a graphical prompt that won't work outside of a graphical environment, and similarly the command-line sudo will not work outside of an interactive shell. Different things for different tasks.

Linux has adopted the Unix philosophy of having a great many tiny tools that do one job very well, and that can be combined together in interesting ways, rather than having to re-do all those functions for every enormous application that you might want to run. In general, these tools are provided by libraries of functions, but the applications themselves are quite small. A simple example would be ```
lspci | grep VGA
```**lspci** simply lists the PCI devices that are connected to your system and spits it to the [standard output]("http://en.wikipedia.org/wiki/Standard_streams#Standard_output_.28stdout.29"). **grep** takes some input and searches for the string that you provide (in this case "VGA") and then prints matches to the standard output. The | symbol represents a pipe that connects the standard output of one thing to the standard input of another thing.

---

### Post by TooCrooked on 2009-08-16
amazing input from both! i'm very thankful.

CK, i have one question... how does a person import a library into ubuntu? im familiar with libraries in programming, and as such, i expect this isn't exactly like compiling/installing a package?

---

### Post by Bachstelze on 2009-08-16
> **TooCrooked said:**
> amazing input from both! i'm very thankful.

CK, i have one question... how does a person import a library into ubuntu? im familiar with libraries in programming, and as such, i expect this isn't exactly like compiling/installing a package?

What exactly do you mean by "import a library"?

---

### Post by CatKiller on 2009-08-17
> **TooCrooked said:**
> i expect this isn't exactly like compiling/installing a package?

It's exactly like installing a package because that's what you do. Unless you're writing your own programs or compiling you don't need to worry about which libraries you've got installed. The packages usually start with "lib," but if they're needed by a particular package then they'll be pulled in as a dependency. Install some stuff with Synaptic and you'll see how it all works.

---

