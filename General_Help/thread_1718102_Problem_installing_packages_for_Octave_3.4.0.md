---
title: "Problem installing packages for Octave 3.4.0"
date: 2011-03-30
forum: General Help
---

### Post by michaelhagg on 2011-03-30
I'm having a problem loading packages with Octave. I'm brand new to Ubuntu and Linux in general (just installed yesterday!), so I'm sort of lost on what to do.

I've installed Octave 3.4.0 from one of those tar.gz files (after  looking up loads of help on the Internet) because the Ubuntu Software  Center only has 3.2.4. Afterward, I installed QtOctave from the Ubuntu  Software Center.

I subsequently tried to install packages (notably Controls and Signals)  using QtOctave's package installation feature. If I try to use a command  from one of those packages, like "help tf2sos," I get an error saying  the command doesn't exist. Is this because I haven't installed things  correctly? Maybe I don't have some "dependencies" I keep reading about?  Maybe that version of QtOctave isn't compatible with Octave 3.4.0? I'm  completely lost on where to turn.

Any help will be GREATLY appreciated. I'd like to use Octave instead of MATLAB, but I may have no choice at this point.

---

### Post by michaelhagg on 2011-04-02
Problem solved. From the octave command line, type "pkg install" followed by the path and file name of the tar.gz file you wish to install.

For example, in order to install my signals package, I used:

"pkg install /home/michaelhagg/Downloads/signal-1.0.11.tar.gz"

It is worthy to note that some packages have dependencies, and you'll need to install those dependencies before you install your desired package. For this example, signal-1.0.11 required optim and specfun in order to install. A list of available packages and their dependencies can be found at:

[http://octave.sourceforge.net/packages.php](http://octave.sourceforge.net/packages.php)

If you click on "Details" next to the package name, it will call out the dependencies.

I hope this helps someone!

---

