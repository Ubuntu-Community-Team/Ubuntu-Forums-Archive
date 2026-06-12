---
title: "Problem installing deb package."
date: 2011-11-13
forum: General Help
---

### Post by iamfuzzeh on 2011-11-13
I've been having some trouble installing packages, being them the common and user-theme that work together with gnome tweak. 

I'm running 11.10 (Ocelot), just installed gnome on it and I'm trying to skin it, thing is I always get an error installing those packages

This is the error itself:

```
Ocorreu um erro não manipulável
A non manipulable error has ocured

Parece que existe um problema no aptdaemon, a aplicação que lhe permite  instalar ou remover programas e executar outras tarefas relacionadas com  a gestão de pacotes.
There seems to be a problem in aptdaemon, the application that lets you install or remove....

Details:

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1028, in _simulate_helper
    deb = self.install_file(trans, simulate=True, **trans.kwargs)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 532, in install_file
    deb = self._check_deb_file(path, force, trans.uid)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1147, in _check_deb_file
    "\n%s" % (path, stdout))
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 46: ordinal not in range(128)

```What I've tried upon using google and searching several threads here:

sudo apt-get update
sudo apt-get upgrade´
ran the broken filter in synaptic, which returns nothing
 sudo dpkg --configure -a

This seems to happen only with those deb packages, I have tried using the program center to install something completely unrelated and no problems occurred.

Any thoughts ?

EDIT:
Upon further searching I found this:

[COLOR=#c20cb9]**sudo**[/COLOR] add-apt-repository ppa:ricotz[COLOR=#000000]**/**[/COLOR]testing [COLOR=#c20cb9][B]
sudo[/B][/COLOR] [COLOR=#c20cb9]**apt-get**[/COLOR] update [COLOR=#c20cb9][B]
sudo[/B][/COLOR] [COLOR=#c20cb9]**apt-get**[/COLOR] [COLOR=#c20cb9]**install**[/COLOR] gnome-tweak-tool gnome-shell-extensions-user-theme

Tested it, and it worked, thanks anyway guys.

---

