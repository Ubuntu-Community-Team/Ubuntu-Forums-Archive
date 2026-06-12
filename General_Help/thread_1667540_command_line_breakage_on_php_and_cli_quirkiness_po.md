---
title: "command line breakage on php and cli quirkiness possibly readline related"
date: 2011-01-15
forum: General Help
---

### Post by jzacsh on 2011-01-15
[SIZE="3"]Questions for this Thread[/SIZE]
[LIST]
[*]which debian/ubuntu package the below issues is a bug for (*necessary to file bugs now, via `apport-bug`*)
[*]If both of my below CLI issues are caused by that same issue
[/LIST]

[SIZE="3"]_CLI ISSUE #1: PHP output quirkiness_[/SIZE]
I described some weird command-line behavior, that happens **only on Ubuntu**, in a _[video]("http://dl.dropbox.com/u/9211525/drush-help-less.ogv")_ for _[this Drupal bug]("http://drupal.org/node/877916")_.  It was decided that the problem is in Ubuntu, and not in PHP or in Drupal's script I filed against.

[SIZE="2"]ISSUE #1, Information:[/SIZE]
[LIST]
[*]_[comment #1288376226 (on php.net)]("http://bugs.php.net/bug.php?id=48125#1288376226")_ about different compile methods of php-cli between Ubuntu and Debian seems to have spawned all kinds of threads and issues about mysql-cli and CTRL-R (*reverse search history*)
[*]Ubuntu 10.04 seems to be the only one that has the problem. Between the drupal bug and the php.net bug (i think) its safe to say that this has been tested in arch linux, debian, OSX, and Ubuntu 10.04.
[/LIST]

[SIZE="3"]**[COLOR="Red"]SOLVED[/COLOR]** [COLOR="DimGray"]_CLI ISSUE #2: ~/.inputrc not inherited in applications_[/COLOR][/SIZE]
*[COLOR="Red"]solved: [http://ubuntuforums.org/showpost.php?p=10393024&postcount=5](http://ubuntuforums.org/showpost.php?p=10393024&postcount=5)[/COLOR]*
Applications with their own prompt seem to behave strangely in Ubuntu.
_**Example applications**_: mysql's command line client and python's command line interpreter.
_Expected behavior_:
I have my output set to vi, in my [~/.inputrc]("https://github.com/jzacsh/dotfiles/raw/master/.inputrc") file, among other things, this means my up/down history is binded to [j]/[k] keys. In Arch Linux, when I open either of the above mentioned apps, I can continue taking advantage of these nice bindings, just as I was a moment ago on the bash command line.
_Ubuntu Buggy behavior_:
Using the same [~/.inputrc]("https://github.com/jzacsh/dotfiles/raw/master/.inputrc") file, when I open either of the above mentioned apps, nothing happens when I hate [j] or [k]

[SIZE="2"]ISSUE #2, Information:[/SIZE]
[LIST]
[*]if _[comment #1288376226 (on php.net)]("http://bugs.php.net/bug.php?id=48125#1288376226")_ about different compile methods of php-cli is true, then it would explain why my ~/.inputrc (see ISSUE 1, above) config has problems in ubuntu.
[*]Between the drupal bug and the php.net bug (i think) its safe to say that this has been tested in arch linux, debian, OSX, and Ubuntu 10.04. Ubuntu 10.04 is the only one that has the problem.
[/LIST]

_*[SIZE="3"]Things that seem, or are related:[/SIZE]*_
[LIST]
[*][http://bugs.php.net/bug.php?id=48125](http://bugs.php.net/bug.php?id=48125)
[*][https://bugs.launchpad.net/ubuntu/+source/mysql-5.1/+bug/633129](https://bugs.launchpad.net/ubuntu/+source/mysql-5.1/+bug/633129)
[*][http://drupal.org/node/877916](http://drupal.org/node/877916)
[*]I'm using Ubuntu 10.04 on two differnet 64bit installs machines.
[/LIST]

Anyone have suggestions, more info I could gather, or generally which package I can post about to launchpad.net/ubuntu?

---

### Post by jzacsh on 2011-01-18
bump

---

### Post by jzacsh on 2011-01-18
bump

[edit]
sorry this is a duplicate. ubuntuforums.org was taking over a minute to respond.

---

### Post by jzacsh on 2011-01-23
bump

---

### Post by jzacsh on 2011-01-24
Turns out CLI ISSUE #2 is no longer an issue I simply did not have my ~/.inputrc file in place. However CLI ISSUE #1 is still being looked into by myself and some in #ubuntu-server. If you have any thoughts on what to try, please let me know.

_Current attempt:_
I will be recompiling `php` and then `less` in two separate tests in a VM to see if I can reproduce this from a distribution that does *not* inherently have the issue (*eg.: archlinux*).

---

