---
title: "Bash doesn't see my aliases. Thought I had fixed it."
date: 2009-06-27
forum: General Help
---

### Post by Lostin60's on 2009-06-27
I just did a fresh clean install of Jaunty,and thought I had this solved.  In the course of trying to add some aliases, I missed seeing the > ~/.bashrc file.  I know...dumb mistake.  The result was that in trying to find a work around (still thinking I had a missing file) I messed up some files, and renamed others.  At any rate, I fixed the files, and aliases should be working, but they aren't.

  I found a lot of advice on the web, but all of it boiled down to > uncomment the following lines which I had already done.  

I tried all the different combinations of commenting and uncommenting  the > .bash_aliases and  > bash_completion  portions of the file.

  And I think I checked all the associated files in the > /usr/>>>>/(bash something) and 
 > /etc/>>>>>/(bash something) paths. 

It's possible I missed one, but the ones I checked seem to be fine.  Of course that  evaluation comes from a somewhat informed, but still very green noob. 

I also ran ```
source ~/.bashrc
``` Below is my corrected file as it stands now.


```
# ~/.bashrc: executed by bash(1) for non-login shells.

# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)

# for examples



# If not running interactively, don't do anything

[ -z "$PS1" ] && return



# don't put duplicate lines in the history. See bash(1) for more options

# don't overwrite GNU Midnight Commander's setting of `ignorespace'.

export HISTCONTROL=$HISTCONTROL${HISTCONTROL+,}ignoredups

# ... or force ignoredups and ignorespace

export HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it

shopt -s histappend



# check the window size after each command and, if necessary,

# update the values of LINES and COLUMNS.

shopt -s checkwinsize



# make less more friendly for non-text input files, see lesspipe(1)

#[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"



# set variable identifying the chroot you work in (used in the prompt below)

if [ -z "$debian_chroot" -a -r /etc/debian_chroot ]; then

    debian_chroot=$(cat /etc/debian_chroot)

fi



# set a fancy prompt (non-color, unless we know we "want" color)

case "$TERM" in

xterm-color)

    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

    ;;

*)

    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

    ;;

esac



# Comment in the above and uncomment this below for a color prompt

#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '



# If this is an xterm set the title to user@host:dir

case "$TERM" in

xterm*|rxvt*)

    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'

    ;;

*)

    ;;

esac



# Alias definitions.

# You may want to put all your additions into a separate file like

# ~/.bash_aliases, instead of adding them here directly.

# See /usr/share/doc/bash-doc/examples in the bash-doc package.



if [ -f ~/.bash_aliases ]; then

   . ~/.bash_aliases

fi

# ~/.bashrc: executed by bash(1) for non-login shells.

# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)

# enable color support of ls and also add handy aliases

if [ "$TERM" != "dumb" ]; then

    eval "`dircolors -b`"

    alias ls='ls --color=auto'

    #alias dir='ls --color=auto --format=vertical'

    #alias vdir='ls --color=auto --format=long'

fi



# some more ls aliases

#alias ll='ls -l'

#alias la='ls -A'

#alias l='ls -CF'



# enable programmable completion features (you don't need #to enable this, if it's already enabled in #etc/bash.bashrc and /etc/profile
#source /etc/bash.bashrc

if [ -f /etc/bash_completion ]; then

    . /etc/bash_completion

fi
```

If I uncomment the ```
#alias ll='ls -l'
``` line from the file bash doesn't see that alias either.  

> # See /usr/share/doc/bash-doc/examples in the bash-doc package.
I have no > /usr/share/doc/bash-doc
Also
> # enable programmable completion features (you don't need #to enable this, if it's already enabled in #/etc/bash.bashrc and /etc/profile
It is enabled in > /etc/bash.bashrc but not even mentioned in > /etc/profile”

Any and all help with this will be  greatly appreciated.
[COLOR="White"]aa[/COLOR]

---

### Post by Brandon Williams on 2009-06-27
How are you starting bash? Is it running as a login shell? If so, then your .bash_profile or .bash_login or .profile will be sourced (whichever is encountered first, in that order). If you want your .bashrc file have an impact for a login shell, then you must explicitly source it in whichever one of the profile files you use.

/etc/profile sources /etc/bash.bashrc, which should mean that anything you are counting on from /etc/bash.bashrc is there no matter how you start bash.

---

### Post by v3xtra on 2009-06-27
If you comment out the part about bash_aliases, then why aren't you putting your aliases in there?  I think it is trying to look for aliases in that file, but there aren't any, so it's not working.  Try making that file and putting them in there.  It works fine for me.

---

### Post by capscrew on 2009-06-27
As v3xtra has said, the pertinent section is```
# Alias definitions.

# You may want to put all your additions into a separate file like

# ~/.bash_aliases, instead of adding them here directly.

# See /usr/share/doc/bash-doc/examples in the bash-doc package.



if [ -f ~/.bash_aliases ]; then

   . ~/.bash_aliases

```

The above says: if there is a file in your home directory called .bash_aliases; then read it into memory and use those aliases.  But, you have to have the file and it has to have the alias you want in it.  

With the section uncommented you should create a .bash_aliases file in your home directory.  You can use your favorite text editor to create, edit and add your aliases to the file.

Here are some of the aliases i have in my .bash_aliases file```
# Exit the terminal
alias x='exit'

# Desktop
alias desktop='cd ~/Desktop'

# Modified ping command
alias ping='ping -c4'

# Directory Commands
alias ll='ls -lh'
alias la='ls -Ah'
alias l='ls -CFh'
alias lla='ls -lah'
alias dir='ls -lah'

# Display path
alias path='echo $PATH'

# File Commands
alias rm='rm -i'
# alias rmr'sudo rm-r'


# Clear Screen
alias cls='clear'
alias c='clear'

# Grep Commands
alias g='grep --color=auto'
alias rg='rgrep --color=auto'

```

---

### Post by kerry_s on 2009-06-27
make sure you don't have the terminal open, if so restart it than try.

i just use ~/.bashrc for mine.

---

### Post by Lostin60's on 2009-06-27
> **v3xtra said:**
> If you comment out the part about bash_aliases, then why aren't you putting your aliases in there?  I think it is trying to look for aliases in that file, but there aren't any, so it's not working.  Try making that file and putting them in there.  It works fine for me.

I assume you mean if I am commenting out bash_aliases why aren't I putting my aliases in.bashrc? 

My bash_aliases are not commented out. And I am using .bashrc as my source and bash_completion is also not commented out.  However, looking at it again just now, I have source bash_completion commented out. Fixing that now.

---

### Post by Lostin60's on 2009-06-27
> The above says: if there is a file in your home directory called .bash_aliases; then read it into memory and use those aliases. But, you have to have the file and it has to have the alias you want in it.

Capscrew, I want to thank you. I was pretty sure that that is what that code meant, if translated into English. I just double checked my ~/.bashrc and I don't have "source" for bash_completion commented out.  I really had fouled up my ~/.bashrc badly and pretty much just went by common sense to put it right.  I am real new to this, so it takes me a bit to figure out what I _think_ it means.  Got lucky this time. 

Your answer along with brandons and kerry's gives me yet another question.

Ok....... never mind for now, I closed my terminal and reopened it and my aliases and my auto completion are working fine. So, my new question, is WHY? 

 I know it has something to do with how I start up.  But is that how I start my session, or my terminal. I am still wrapping my mind around the whole shell thing. But I was under the impression that bash scripts ran immediately.  I mean nothing needed to be re-started for them to run.

I really appreciate the help, and especially that the three of you *explained* what the coding meant.  Actually knowing what it meant is probably more useful than just getting the code.  It's that "give a man a fish thing".  I really do need to read up on the shell thing, though.  I think it's going to be one of those things that are simple in concept, but difficult in execution.

And again, thanks for all the help.
[COLOR="White"]aa[/COLOR]

---

### Post by kerry_s on 2009-06-27
if you screw up the bashrc, there is a exact copy in /etc/skel that you can copy.

---

### Post by Lostin60's on 2009-06-27
> **kerry_s said:**
> if you screw up the bashrc, there is a exact copy in /etc/skel that you can copy.

My, what a timely reply...:lolflag:  I had actually discovered that......AFTER I had the file put back together.  None the less, your reply is appreciated.
[COLOR="White"]aa[/COLOR]

---

### Post by Lostin60's on 2009-06-27
Quickie question. I can't google it, cuz google ignores punctuation.  Is ~/ the same as /home/usrname?  And if there is a difference, how are they different?  I know...my questions are getting really basic, but I gotta start somewhere.  Gonna go look for a couple good bash tuts right now.
[COLOR="White"]aa[/COLOR]

---

### Post by kerry_s on 2009-06-27
> Is ~/ the same as /home/username?

yes

---

### Post by JKyleOKC on 2009-06-27
> **Lostin60's said:**
>  Gonna go look for a couple good bash tuts right now.
[COLOR="White"]aa[/COLOR]The best one I've seen is a book from O'Reilly titled "Learning the bash shell" which goes into total detail, but takes it just a few steps at a time so that you're never completely lost. I believe there's an excerpt from it on-line, together with the examples that you work out in each chapter...

---

### Post by capscrew on 2009-06-28
> **Lostin60's said:**
> Capscrew, I want to thank you. I was pretty sure that that is what that code meant, if translated into English. I just double checked my ~/.bashrc and I don't have "source" for bash_completion commented out.  I really had fouled up my ~/.bashrc badly and pretty much just went by common sense to put it right.  I am real new to this, so it takes me a bit to figure out what I _think_ it means.  Got lucky this time.

I'm glad you go it sorted out.  One thing that is hard for users new the unix way to understand is that "common sense" doesn't always work out.  You need to understand how the system works and apply "unix common sense".
> 

Your answer along with brandons and kerry's gives me yet another question.

Ok....... never mind for now, I closed my terminal and reopened it and my aliases and my auto completion are working fine. So, my new question, is WHY? 

The reason has to do with what happens when a bash shell is opened by the user.  When you open a new shell in the terminal the shell reads the aliases into memory.  When you invoke them you are doing it from memory not the file.

The /etc/bash_completion for the user to view what commands are available with the users partial input.  It does not complete the command.  You can invoke bash_completion by hitting the tab key twice.  After entering this```
pi
```Hit the tab key once and then again.  Why twice; what if you wanted to enter a tab in the shell?> 

 I know it has something to do with how I start up.  But is that how I start my session, or my terminal. I am still wrapping my mind around the whole shell thing. But I was under the impression that bash scripts ran immediately.  I mean nothing needed to be re-started for them to run.

Aliases are called from memory and are not a script and bash_completion is called with the tab key.> 

I really appreciate the help, and especially that the three of you *explained* what the coding meant.  Actually knowing what it meant is probably more useful than just getting the code.  It's that "give a man a fish thing".  I really do need to read up on the shell thing, though.  I think it's going to be one of those things that are simple in concept, but difficult in execution.
Absolutely!  But the knowledge always leads to more questions and more knowledge. :-)   > 

And again, thanks for all the help.
[COLOR="White"]aa[/COLOR]

Edit: The GNU manual for bash is [http://www.gnu.org/software/bash/manual/]("http://www.gnu.org/software/bash/manual/")

---

### Post by Lostin60's on 2009-06-28
> **JKyleOKC said:**
> The best one I've seen is a book from O'Reilly titled "Learning the bash shell" which goes into total detail, but takes it just a few steps at a time so that you're never completely lost. I believe there's an excerpt from it on-line, together with the examples that you work out in each chapter...

Thank you, sir.  Muchly appreciated.  I did find this site  [http://bash-hackers.org/wiki/doku.php/scripting/tutoriallist]("http://bash-hackers.org/wiki/doku.php/scripting/tutoriallist")  which led me to a couple of very promising sites.  It's a good place to recommend for folks looking for on-line tutorials.

I am rather "between a rock and a hard place" at the moment.  I'm pretty new to Ubuntu. Just moved up from Intrepid, and did a clean (we love you, killdisk) install of Jaunty.

  So I have a new distro, and the occasional bug that goes along with a new distro. (quick aside: hats off to the dev team. I was floored to see how quickly bugs were being fixed.)

 I am getting my box all tweaked out, which in itself is a whole new learning experience.  I am determined to get proficient in bash.  And I am trying to become as mouseless as I can.  And then there's Compiz, and Emerald, and Zimbra, and..and..and Lions and tigers and b....sorry, went a bit sideways there.

I have always been a bit...well let's just say I will never be mistaken for Job.:mrgreen:, and it's a bit rough trying to learn it all at once.  I am, however, enjoying the living hell outa it.

So I am appreciative of you and the others who have been so helpful.  A year from now I hope to be the askee rather than the asker.
[COLOR="White"]aa[/COLOR]

---

### Post by Lostin60's on 2009-06-28
Edit: The GNU manual for bash is [http://www.gnu.org/software/bash/manual/]("http://www.gnu.org/software/bash/manual/")[/QUOTE]

Thanks Capscrew. That was very informative. I guess the term "common sense" IS pretty subjective.  I have always taken it to mean *applying* logical thinking along with intuitive reasoning. It really does take all 3.  

I had a professor many years back, teaching a Pascal class. For the life of me I can't remember his name, but he had written a very widely used book on Pascal programming. Guess which book we used in class?  So here we sat in class, trying to learn modular programming out of a book that made "spaghetti code" look sensible in comparison.  I mean to call it badly written would almost be complimentary.  The man had logical thinking, and intuitive reasoning.  He was, however, sadly lacking in the application department.

But, I digress.  You hit the nail on the head about the answers always leading to more questions. And I am very much a "why??" kind of person. I drove my geometry teaches nuts.  I kept wanting him to explain the 5 postulates...lol.

Well, thanks again one and all. I am off to horizontal land.
[COLOR="White"]aa[/COLOR]

---

### Post by dromichaetes on 2009-06-30
> **Lostin60's said:**
> If I uncomment the ```
#alias ll='ls -l'
``` line from the file bash doesn't see that alias either.  

**# See /usr/share/doc/bash-doc/examples in the bash-doc package.**                   
         
I have no 

** /usr/share/doc/bash-doc**             


Bash-doc: "This package contains the distributable documentation, all the
examples and the main changelog." 

You have to install the bash-doc package if you want it to appear in /usr/share/doc/. You can search for **bash-doc** in synaptic or you can simply use the terminal:
```
sudo apt-get install bash-doc
```
But you must've figured that out by now... :)

---

### Post by Lostin60's on 2009-07-01
> **dromichaetes said:**
> Bash-doc: "This package contains the distributable documentation, all the
examples and the main changelog." 

You have to install the bash-doc package if you want it to appear in /usr/share/doc/. You can search for **bash-doc** in synaptic or you can simply use the terminal:
```
sudo apt-get install bash-doc
```
But you must've figured that out by now... :)

Thanks for the info.  And, actually, I hadn't.  I just thought it was a glitch.  I didn't think that a package that was sourced (I'm pretty sure I saw it sourced somewhere) wouldn't be included in the install.  And since it said examples I didn't think it would have anything executabe in it.  Live and learn.  Any way, I have it installed now, and I think I will gain some insight with it.  I appreciate the post...feel free to toss in any thoughts you may have in the future.

Just as an aside... I am 58.  Back in '05 and '06 I was working in Afghanistan for a company called KBR.  You may have heard of them..lol. We had a shop for each trade and took care of the laundry and chow hall.  At the end of '06 I developed a lot of pain in my legs. 

After I went to the company medics the second time about it they took me to the base hospital.  I was sitting on a gurney and the Doc came in.  All he did was look at me, and said, "We're med-i-vacing to Germany immediately."  I said, "OK" and it was like someone hit my off switch.  My next memory was waking up in the hospital 8 days later.  

Long story short, it seems that HepC caught up with me.  Took a year to get on the chemo. 48 absolutely miserable weeks on the chemo. And the chemo didn't take...wheee. Last week I found out that the small tumor on my liver had metastasized. So now it's radiology and if that doesn't work, a liver transplant.  Never in a million years did I expect cancer.  Ah, well, at least it won't spread.

I have worked since I was 15.  Now, in Oct. I have spent 3 years just sitting.  And I hate it.  You get to feeling useless...maybe worthless is a better word.  At any rate getting out of Windows and into a system where there is so much to learn is turning out to be excellent therapy.  I plan to learn bash, C++, and a little java-script and Pearl.  This is the best I have felt since I got back stateside.

Basically, I said all that so folks will understand that if they have any comments, or advice, they can feel free.  Unsolicited advise is welcome.  I won't feel that anyone is poking their nose where it doesn't belong.  Some folks are kinda thin skinned about that.  I'm not one of them..lol.

Again thanks to all for the help.
[COLOR="White"]aa[/COLOR]

---

### Post by Lostin60's on 2009-07-01
> How are you starting bash? Is it running as a login shell? If so, then your .bash_profile or .bash_login or .profile will be sourced (whichever is encountered first, in that order). If you want your .bashrc file have an impact for a login shell, then you must explicitly source it in whichever one of the profile files you use.
/etc/profile sources /etc/bash.bashrc, which should mean that anything you are counting on from /etc/bash.bashrc is there no matter how you start bash. 



Well, I am starting to get a little better handle on this.  I thought that figuring out Brandon's questions would be a good starting point.
  > /etc/profile sources /etc/bash.bashrc   threw me for a loop...untill I realized that it was a *sentence* and not a  line of code I had to put somewhere.   
 That clarified things a LOT...lol.    At first I had no idea how I was starting bash.  So I went to find .bash_profile. I used “search” in the file browser and “locate” in the terminal, and found I don't have one.  The same for .bash_login.  I did have a dot.bash_profile, so I checked it out.

>  # This script file is executed by bash(1) for login shells.  By default,

# it does nothing, as ~/.bashrc is already sourced by /etc/profile.
 
#
Now I know bash is running as a login shell.  I still need to understand the concept better, though.
```

[o/s
	{shell
			
		(kernel)
	}
]

```
  BTW, did I “code” that right?  For instance if it were nested if/then statements?   The concept of sourcing I well understand.  And *what* to source is pretty straight forward.  But, *where* to source it at is a whole 'nuther thang..lol.  

Back in the day, I did have a couple semesters of C.O.B.A.L. one semester of Pascal, and was just getting into JCL when circumstances arose that made me have to quit.  I was pulling about a 3.7 or 3.8 GPA.  Woulda been 3.9 if it weren't for accounting.  Time constraints dictated that I had to let *something* slide. Getting up at 5:30 a.m. for work...getting home from school after midnight.  But I digress..lol.

Then I checked out /etc/profile.  I think the first nested if/then was saying to run bash interactively?  The second one sourced /etc/bash.bashrc.  I looked at it for a good while, and taking into account the fact that while I don't know bash's coding, I have a bit of a notion of how the syntax should go, I have a question.




```
 
[COLOR="Yellow"]if [ "$PS1" ]; then[/COLOR]

  [COLOR="Blue"]if [ "$BASH" ]; then

    PS1='\u@\h:\w\$ '[/COLOR]

    [COLOR="Red"]if [ -f /etc/bash.bashrc ]; then

	. /etc/bash.bashrc

    fi[/COLOR]

 [COLOR="Blue"] else[/COLOR]

    [COLOR="Green"]if [ "`id -u`" -eq 0 ]; then

      PS1='# '

    else

      PS1='$ '

    fi[/COLOR]

  [COLOR="Blue"]fi[/COLOR]

[COLOR="Yellow"]fi[/COLOR]



umask 022
``` 


That in red seems to be a closed if/then nested in the blue. The green is also nested in the blue, and the whole thing is nested in the yellow.  Obviously the code is right, because it works. But why doesn't the line ```
 PS1='\u@\h:\w\$ '

```
Have an “else” at the end?  To me it says >  if $SP1 is true then check if  $BASH is true and if it is then do PS1='\u@\h:\w\$' but if $BASH is false then do all of green then close blue then close yellow  which leaves the source just hanging there.... a closed if/then with nothing to tell it to execute.

I am going to leave it at just that question for now, and I am going back to looking to see what is sourced where.  I also have to get into my tuts.  I think that trying to work out code that is already there will be a great help with the tuts.  It will give me a notion of what is to come before I actually get there in the tuts.
[COLOR="White"]aa[/COLOR]

---

### Post by capscrew on 2009-07-01
> **Lostin60's said:**
> Well, I am starting to get a little better handle on this.  I thought that figuring out Brandon's questions would be a good starting point.
    threw me for a loop...untill I realized that it was a *sentence* and not a  line of code I had to put somewhere.   
 That clarified things a LOT...lol.    At first I had no idea how I was starting bash.  So I went to find .bash_profile. I used &#8220;search&#8221; in the file browser and &#8220;locate&#8221; in the terminal, and found I don't have one.  The same for .bash_login.  I did have a dot.bash_profile, so I checked it out.


Now I know bash is running as a login shell.  I still need to understand the concept better, though.
```

[o/s
	{shell
			
		(kernel)
	}
]

```
  BTW, did I &#8220;code&#8221; that right?  For instance if it were nested if/then statements?   The concept of sourcing I well understand.  

Sort of, but then again not so.  Think of it more like a circle (or a piece fruit).  there is a core (kernel) and around the core is the flesh (O/S) and a specific tool  (the shell (and in out cash this is the bourne again shell (bash))).
> 

And *what* to source is pretty straight forward.  But, *where* to source it at is a whole 'nuther thang..lol.  

Back in the day, I did have a couple semesters of C.O.B.A.L. one semester of Pascal, and was just getting into JCL when circumstances arose that made me have to quit.  I was pulling about a 3.7 or 3.8 GPA.  Woulda been 3.9 if it weren't for accounting.  Time constraints dictated that I had to let *something* slide. Getting up at 5:30 a.m. for work...getting home from school after midnight.  But I digress..lol.

Then I checked out /etc/profile.  I think the first nested if/then was saying to run bash interactively?  The second one sourced /etc/bash.bashrc.  I looked at it for a good while, and taking into account the fact that while I don't know bash's coding, I have a bit of a notion of how the syntax should go, I have a question.

```
 
[COLOR="Yellow"]if [ "$PS1" ]; then[/COLOR] **#primary shell**

  [COLOR="Blue"]if [ "$BASH" ]; then

    PS1='\u@\h:\w\$ '[/COLOR] **#if the shell is bash use this prompt**

    [COLOR="Red"]if [ -f /etc/bash.bashrc ]; then

	. /etc/bash.bashrc **[COLOR="Black"]# if the file /etc/bash.bashrc exists; source it (read into memory )[/COLOR]**

    fi[/COLOR]

 [COLOR="Blue"] else[/COLOR]  

    [COLOR="Green"]if [ "`id -u`" -eq 0 ]; then

      PS1='# ' **[COLOR="Black"]If the user is root, the use this prompt[/COLOR]**

    else

      PS1='$ ' **[COLOR="Black"]#if not then use this other one[/COLOR]**

    fi[/COLOR]

  [COLOR="Blue"]fi[/COLOR]

[COLOR="Yellow"]fi[/COLOR]



umask 022
``` 


That in red seems to be a closed if/then nested in the blue. The green is also nested in the blue, and the whole thing is nested in the yellow.  Obviously the code is right, because it works. But why doesn't the line ```
 PS1='\u@\h:\w\$ '

```

Have an &#8220;else&#8221; at the end?  To me it says   which leaves the source just hanging there.... a closed if/then with nothing to tell it to execute.

See my inline comments above in bold.> 

I am going to leave it at just that question for now, and I am going back to looking to see what is sourced where.  I also have to get into my tuts.  I think that trying to work out code that is already there will be a great help with the tuts.  It will give me a notion of what is to come before I actually get there in the tuts.
[COLOR="White"]aa[/COLOR]

Keep working at it Lostin60's

Your questions are interesting to answer.  The notion of a shell has complexity.  It is the interface to the O/S, but is also a rich programing environment.  one shell can spawn another and when you run a shell script in the background you have a non-login shell.  

It might help if you try to not think of these things in a physical way.  They are virtual notions and don't have to work like the names imply in the physical world.  The names are for humans to be able to discuss the concepts.

---

### Post by JKyleOKC on 2009-07-01
Getting a firm handle on the concepts of kernel, o/s, and shell is a very good place to start and will make it much easier for you to proceed! There are lots of ways to view the relationships, though. I'll offer you a different view:

Imagine, if you can, a box that has only the CPU, the RAM, a monitor, a keyboard, but no software. It would have no way for keystrokes to make their way to the CPU and make something happen, nor for any results to get to the monitor for you to see. There has to be at least some basic software there, to tie everything together.

The most basic stuff is known as the Basic Input Output System or BIOS, and it's what runs automagically when you boot the box. However it IS extremely basic and knows nothing of any commands, so it must load more sophisticated software into RAM before you can use the system. This second-level software is what we call the operating system or o/s, but like all advanced things it's made up of many components.

The component that mediates between the BIOS and the rest of the o/s is the kernel; it's called that because it's like a kernel of corn -- a seed from which everything else springs. However the kernel, like the BIOS, is still pretty primitive and you can talk to it only in machine language. It doesn't know much human language!

Enter another component to mediate between the kernel (actually all the rest of the o/s) and you, the operator. That's the shell. Its entire purpose is to facilitate your communication with the other parts of the o/s. Every o/s that deals with human operators has a shell of some sort; other systems often call it the "command processor" which is a bit more descriptive of its purpose. In Windows, it's "command.com" or "cmd.exe" in newer versions. In older IBM mainframes it was JCL or Job Control Language. In Linux you can choose between a number of different shell programs. The original was simply "sh" for "shell" but it was a bit primitive. Over the years many others were built; "bash" is simply the one that's now most common and the one that the flavors of Ubuntu use by default. It has all sorts of special features that make communication with the system easier and meet special needs. Don't try to learn them all at once; like most anything else, master the complexity by "divide and conquer" -- that is, learn what you need to do what you want, and explore added features as you need them.

The main thing the shell does is to process commands from you to the system. Each command is either a built-in bash command, or the name of a program to be loaded and executed. You can get a list of the built-in commands from any of the documents already referenced, but in practice there's no need to know which is which because both kinds of commands do things in essentially the same way. When you type in a command, the shell parses it into its own language, then launches the requested software if it exists (and lets you know if it does not). When the software finishes, it turns control back to the shell, which then gives you another prompt and waits for your next input.

From this viewpoint, it looks as if the shell is running inside the o/s but alongside the kernel, which is there in the background like a trusty slave to do whatever its master asks to be done.

You can get a good idea of the complexity of things by running the command "top" from a CLI prompt; the leftmost column shows the process identifier or PID of each separate process that's running. You'll see that PID 1, "init" is always there. That's the initialization command that handles the boot process and then runs in background to handle logging in, running the shell, and everything else. You'll also be amazed, probably, at the number of processes running even when you're "doing nothing." Most of these simply do necessary housekeeping; many of them are parts of the kernel and only a few are parts of the shell.

I hope this helps you grok the concepts involved. It's always confusing at first, since the GUI (another layer that runs under the shell and transforms mouse movements into shell actions) tends to hide all the complexity. Since I learned computers back in the days of panel switches and punched paper tape, I picked up each layer as it came into use and that has made it much simpler for me. Perhaps I can pay forward some of the help I got many years ago by helping clear up some of the fog for others...

---

### Post by bab1 on 2009-07-01
> The component that mediates between the BIOS and the rest of the o/s is the kernel; it's called that because it's like a kernel of corn -- a seed from which everything else springs. However the kernel, like the BIOS, is still pretty primitive and you can talk to it only in machine language. It doesn't know much human language!

To clarify this a little; the BIOS is only involved in the starting of the computer (bootstrapping).  Once the machine has POSTed, the kernel is booted and the BIOS is done.

---

### Post by Brandon Williams on 2009-07-01
> **Lostin60's said:**
> Well, I am starting to get a little better handle on this.  I thought that figuring out Brandon's questions would be a good starting point. At first I had no idea how I was starting bash.

The basic idea here is that the shell might be started as a result of a console-based login (a login shell) or it might be started some other way ... a new instance of the shell that was started to run a script (a non-interactive, non-login shell) or to provide a command-line in a terminal-emulator (an interactive, non-login shell). The initialization that is done when the shell is run as a login shell is different from the initialization that is done when it is not run as a login shell, and the initialization that is done for an interactive non-login shell is different from what is done for a non-interactive non-login shell (phew!).

Making matters even more complicated, the shell can be run as if it were a login shell, even when it is not really a login shell. This can be done by specifying the -l flag on the command line when the shell is started, or it can be done for you by your terminal-emulator (see the 'Title and Command' tab of the gnome-terminal 'Edit Profile' dialog). The initialization that is done for a login shell is always the same regardless of whether it is interactive, unless the init file itself has conditional code (as in your example from /etc/profile). On the other hande, the initialization for a non-login shell differs based on whether it is interactive or not.

The default ~/.profile in Ubuntu has the following:
```
# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
        . "$HOME/.bashrc"
    fi
fi
```
which will ensure that you always do all of the interactive shell init specified for a non-login shell when you run a login shell. However, if you delete the default ~/.profile or create either ~/.bash_login or ~/.bash_profile, then you must use code like the above to ensure that your ~/.bashrc is sourced at initialization for a login shell.

---

### Post by JKyleOKC on 2009-07-01
> **bab1 said:**
> To clarify this a little; the BIOS is only involved in the starting of the computer (bootstrapping).  Once the machine has POSTed, the kernel is booted and the BIOS is done.
Not always true; some drivers use BIOS routines to communicate to the actual hardware. However many newer devices (for example, webcams and SATA drives) aren't supported by BIOS and for them, you're right. Actually, these days kernel booting is a multi-stage process in itself, with a rudimentary kernel being loaded into a ramdrive first, in order to load the main kernel and drivers. Removing the "quiet" option in GRUB will show the boot time events; /var/log/dmesg can be viewed to see them at a less frantic pace.

---

### Post by Lostin60's on 2009-07-03
First off, as Tony would say, "You people are GRRRRRRRRREAT!!" It was so nice to have a couple different points of view.  All of your comments really clarified things a lot.  Of course I now have new questions.  Thanks guys:confused::cry::lolflag:

I guess first I need to comment on a couple comments in your replies.

@>>capscrew  
> The reason has to do with what happens when a bash shell is opened by the user. When you open a new shell in the terminal the shell reads the aliases into memory. When you invoke them you are doing it from memory not the file.
I understand the interactive and non-interactive ?modes? Also now I have a better understanding of why folks refer to some programs as memory hogs. And I would guess that has as much to do with coding as it does the size of the program? 
 
When you say "open a new shell in the terminal" does that mean I am running 2 instances of the same  shell? I am getting a better grip (that would be grok to you JKyleOKC) on the fact that shell doesn't mean container. 

As to the explanation of the code.  Some how when I typed "To me it says which leaves the source just hanging there.... a closed if/then with nothing to tell it to execute." the text between "says" and "which" didn't make it to the post..lol.

 Not knowing the language (what the variables meant) I was at a complete loss at to what was going on in parts of the file.  So I color coded it and said what I thought it meant by referring to each statement by color.  I pretty well hit it, except I didn't realize that source meant to read it into memory.  I thought it simply meant to use the information there-in.

Ok, I lied..I knew, because some one had made a point of telling me that, but it just flowed right through the sieve sitting on my shoulders.  But my question remains the same.

If the if/then/else statement stops at```
 PS1='\u@\h:\w\$ '
``` why doesn't ```
if [ -f /etc/bash.bashrc ]; then

	. /etc/bash.bashrc # if the file /etc/bash.bashrc exists; source it (read into memory )

    fi

``` see that as an unfinished if/then statement?  I understand (I think) the the if/then statement referring to bash.bashrc is a little piece of business in and of itself, and would have to be executed even if the prompt statement didn't exist.  

I say that because the bash.bashrc statement has nothing to do  with what overall program calls the prompt. I also think that even though the bash.bashrc *sits* inside the prompt statement it isn't truly *nested.*  Neither of the 2 statements has any dependency on the other. At any rate, that is how I see it. I also know I am wrong.  I just can't figure out why.

```
if [ "$PS1" ]; then #primary shell(understood)

  if [ "$BASH" ]; then

    PS1='\u@\h:\w\$ ' #if the shell is bash use this prompt (also understood but why isn't this construed as an unfinished statement? no fi  no else)

    if [ -f /etc/bash.bashrc ]; then

	. /etc/bash.bashrc # if the file /etc/bash.bashrc exists; source it (read into memory )

    fi

  else  

    if [ "`id -u`" -eq 0 ]; then

      PS1='# ' If the user is root, the use this prompt

    else

      PS1='$ ' #if not then use this other one

    fi

  fi

fi




``` Geeze, the more I look at this, the more confused I get. "If the shell is bash use this prompt, otherwise if the user is root use this prompt otherwise use this other prompt."  And hanging in the middle is "if this file exists, use it."  

If the shell isn't bash shouldn't the program terminate at that point, since it's written for bash. Even if another shell could interpret the commands why would "root or not root" be an ?argument? to "if the shell is bash?"

And if there is a reason for all that why doesn't the program hang at ```
PS1='\u@\h:\w\$ '
``` Shouldn't it look for an end or a continuation of the statement and if one isn't there, just hang? Why would it execute a new command that wasn't nested before finishing the existing command?

I know I seem to be putting the cart before the horse, but I have found that posting questions causes me to slow down and examine the question more carefully.  Also seeing WHY I am wrong on one point seems to clarify other points, even if they seem unrelated.

I think that my worst problem is my typing speed.  For instance, while this doesn't seem to be all that long of a post, it has taken me well over an hour. my left hand is 1/2 nerve dead, and the two fingers that do work don't work very well.  I am pretty much a one finger typist with my left hand.

I usually try to skirt that issue by gaining a lot of expertise at whatever I am doing.  So here I am.  I have a few other questions about the replies I have gotten, but I think they will have to wait on the next post.

Again I thank you all for the suggestions and information.  I can't even begin to tell you what a help it has been.  For one thing I see I need a better understanding of the nuts and bolts of how the system runs before I can make use of the coding I do learn.  However, I remain undaunted.

And with that I bid you all a good-night.
[COLOR="White"]aa[/COLOR]

---

### Post by JKyleOKC on 2009-07-03
It may help clear up the confusion slightly to know that the "fi" statements mark the end of the most recent "if" or "else" statements. When you get to a script that uses a "case" statement, its end will be marked by "esac" but "do" statements end with "done" so it's not always consistent that the statement name is spelled backwards to mark its end and of course not all statements require end markers.

Your confusion about where an "if-then" ends was shared by early compiler designers, and the script you're analyzing is a perfect example of the potential ambiguity. Without the "fi" statement (or something similar in languages other than bash) the machine simply couldn't tell where the innermost "if-then" ended, when one "if" was nested inside of another. Even with "fi" there's still a problem, as you've discovered, so there's another rule: "fi" or its equivalent ALWAYS matches the most recent "if-then" or "else" and when several are nested, you get multiple "fi"s at the end (as in this script).

Other languages have different rules; Pascal, for example, allows only one statement between "then" and "else" and only one following "else" so that the second statement after the "else" is not part of the "if" package. When it needs more than one, the programmer must use a "compound statement" sandwiched between "begin" and "end" so that the "if" sees the "begin...end" as its single statement. The C language, in which most of Linux is written, uses the curly braces "{" and "}" for the same purpose. I find the "if...else...fi" rule for bash to be easier to grok.

I've always found it helpful, when analyzing a complicated program, to print a hard copy and draw color-coded lines from the "fi" back to its "else" and from there back to the "if" so that the nesting becomes a bit more obvious.

Edit: Just noticed your real sticking point of why the script doesn't quit immediately upon noticing that the "$BASH" variable is empty. The reason is that it's still running UNDER bash. This test is to distinguish between the initial run of bash, during the login sequence, and subsequent nested runs, when you run another script or trigger a nested instance of the shell. Your initial login shell that's launched during login continues to run invisibly in the background until you log out, so bash is always there (unless you change to a different shell by editing your login options, something that most people never do).

---

### Post by Brandon Williams on 2009-07-03
> **Lostin60's said:**
> If the shell isn't bash shouldn't the program terminate at that point, since it's written for bash. Even if another shell could interpret the commands why would "root or not root" be an ?argument? to "if the shell is bash?"

The /etc/profile script is used for all Posix shells, not just bash. This includes dash, zsh, and ksh. That's why the script checks for bash and sets the prompt differently for bash vs. the others. 

It's generally useful to indicate whether the user is running a shell with root privilege vs one with regular user privilege. The way the prompt is set for bash provides the user name as part of the prompt. When it's not bash, /etc/profile uses a different method, one that is not bash specific, to indicate whether the shell is running with root privilege.

---

### Post by Lostin60's on 2009-07-06
@>>>Brandon
You and Jim are great tag-team teachers. When Jim answers me, you always pick the one thing that would probably start my next question.
> The /etc/profile script is used for all Posix shells, not just bash. This includes dash, zsh, and ksh. That's why the script checks for bash and sets the prompt differently for bash vs. the others.
 
A small thing, but knowing it makes the big things make more sense.   Still haven't started the  tuts, yet, but that's just a matter of priorities vs available time.  Of course, the fact that my system crashed like the Hindenburg didn't help much.

What I was going to do next was to really study in depth the relationships of the .bashrc .bash_alias .profile, etcetera files.  Who was sourced, who did the sourcing, how the code was written...just wanted to get a good, all-around *feel* for it.  Well, I decided that I wanted to have all the files available at once, for easier comparison.  Either all tiled, or all cascaded, depending.  

I did some searching and found a Compiz plug-in.  You could toggle tile and cascade, and you had flexibility in the layout.  Great!  It had one drawback.  It set the window size when it cascaded.  I would make the "restore" size so I could tile 3X2 on my screen.  I could mix them all up, hit "tile" and bingo, I had a perfect fit.

Then I hit "cascade" and as they cascaded the length became about 80% of my screen size, and the height about 40%.  I fixed them 3 times, with the same result each time.  So...time for a new battle plan.  I looked around and found "window rules", and saw that I could "fix" the size of a window.  So I chose normal for the type, and took a  shot in the dark at the size.  I figured Kentucky windage would get me there eventually.

Never did get to find out.  I enabled "window rules", and it all went South, real quick. I had one folder on my desktop.  I could open it, resize it, drag it around, whatever.  I could click "places", and the drop down menu, and navigate to a file to open.  I could click on anything in a tool/task bar. I could bring up Compiz with shortcut keys and as soon as I clicked on "window rules" to disable it, Compiz closed.  Any thing else I clicked on would log me out.  I tried for an hour to get it to work.  

Finally I gave up and put the Jaunty cd in, and ran it live.  Well, I couldn't find a way to cd /  into my file system or HDD.  I tried telling it "cd /sda\0" and "cd /sda0" and a couple other things, all to no avail.  Then I discovered "cd //" did a "dir" and saw "media".  so from the "//$" prompt "cd/media" another "dir" and I saw "disk" another "cd /" and "dir" and I was looking at all my files.

 I mean at the start, from the ubuntu@ubuntu:~$ prompt I could click on "79 GB Media" and see my files, but I couldn't manipulate them in any way.  From the ubuntu@ubuntu:~//media/disk/$ I could.

I navigated to the icon to start a terminal.  I took out the "tile" plug-in and everything associated with it.  Then to be on the safe side, I did the same to compiz.  So I logged out of the live session, restarted my computer , and lo and behold....compiz and the tile plug-in were still there.  

I'm getting it set up to my liking now.  I get all the pretties going, the cube, and decorate the windows.  When the cube spins, Capt. America is the skydome.  Then I go to work on shortcuts and layouts.  I am almost mouse-less.  And the ability to turn the cube with or without any given window is outstanding.  I learn better in an environment that I create and control myself.


@>>> JKyleOKC

Your reply was excellent...as usual.  Consise, detailed, understandable.  Very nice.  The same is true of Jim.  There are still a lot of little basic things I need..like getting into my HDD from the live cd.(there has to be an easier way)  But I am so far ahead of where I was last week.  Really, I can't tell you how much I appreciate the help you've given. On the other hand, I don't have near enough time to ask all the questions your answers create.:?:

You did see the spot that confused me, but it wasn't quite for the reason you thought.
> Edit: Just noticed your real sticking point of why the script doesn't quit immediately upon noticing that the "$BASH" variable is empty.
I think I need you to explain that.  The empty part.  I need to work on my terminology I think.  For instance
```
if [ "$BASH" ]; then

    PS1='\u@\h:\w\$ '
```
To my understanding (and, please, feel free to correct me) "\u@\h: \w\$" is an argument to "PS1", and that "PS1" is the variable, as it stands for prompt, and is defined in different ways according to the situation. It also makes me think that somewhere upstream (in the language of the source code? or the source code itself?) there exists Prompt='PS1".  So I didn't see "the variable as being empty".  Then again I don't really understand what that means.

> It may help clear up the confusion slightly to know that the "fi" statements mark the end of the most recent "if" or "else" statements. That I understand.  Rather, I understand the concept that an if/then or if/then/else has to be closed. I understand the concept of nesting the statements. It's the means used to achieve meeting those concepts that is somewhat hazy to me. Trying to express what I mean isn't too easy either. I will try this.

```
[COLOR="Yellow"]if [ "$PS1" ]; then[/COLOR]

  [COLOR="Blue"]if [ "$BASH" ]; then

    PS1='\u@\h:\w\$ '[/COLOR] 

    [COLOR="Red"]if [ -f /etc/bash.bashrc ]; then

	. /etc/bash.bashrc 
    fi[/COLOR]

  [COLOR="Blue"]else [/COLOR] 

    [COLOR="Green"]if [ "`id -u`" -eq 0 ]; then

      PS1='# ' 
    else

      PS1='$ ' 

    fi[/COLOR]


  [COLOR="Blue"]fi[/COLOR]

[COLOR="Yellow"]fi[/COLOR]

```
OK, I understand that we're looking at 4 conditional statements. I also understand that typically you open them from left to right and close them from right to left.  Also that the first end statement must coincide with the last begin statement. Now here is where I seem to be misunderstanding something. My understanding is that in a conditional statement the syntax must be
1 open statement (IF) argument(A=B THEN)
2    satisfy condition (C)
3 close statement (FI)

However in nested conditional statements the syntax is:

1 open(IF) argument(A=B) condition(THEN)
2    open(IF) argument(C=D) condition(THEN)
3       answer line 2(E)
4    the line following is a related statement(ELSE)
5       open(IF) argument(F=G) condition(THEN)
6          answer line 5(H)
7       close line 5 statement(FI)
8    close line 2 statement(FI)
9 close line 1 statement(FI)

Where 6 satisfies 5 allowing 5 to close 
AND 5 satisfies 2 allowing 2 to close
AND 2 satisfies 1 allowing 1 to close
So we have a situation where each statement satisfies the immediately preceding statement. And that being the case, I don't see how the .bashrc runs.
BTW, I had that all nicely indented in the message box. I think I know what happened, but I am too tired to fix it.

Well, I am about shot out. I will check back in tomorrow.):P
[COLOR="White"]aa[/COLOR]

---

### Post by loomsen on 2009-07-06
Your trying to test statements which don't have anything to do with each other.

```

if [ -f /etc/bash.bashrc ]; then
      . /etc/bash.bashrc 
fi

```

will source everything in the file above if it exists. So this code is included. Now your .bashrc will be read, and in case you specified any overrides for any variables these will override what you just sourced.
So
if [ "$BASH" ]
this is not a real test, it will always return true as you're not testing the argument against something.

if [ "$BASH" == "/bin/bash" ];then 
   do something
elif [ "$BASH" == "/bin/ksh" ];then
   do something else
else
   echo "Unknown bash?"
fi

Let's assume your $PS1 is set to \u@\h

If you want to change the prompt depending on the user id, you'll need to include the current $PS1, otherwise setting 
PS1='# '
will completely override what was before, setting 
$PS1 to #

So your prompt will look like

# 

PS1='$PS1 # ' 

will include the $PS1 so far  (as assumed \u@\h) making your prompt look like

\u@\h # 

But note that if you're including the UID check inside your ~/.bashrc this _WON'T_ apply to root.

```

# ======== Custom prompt
# Define colors for readability
#black="\[\033[0;30;49m\]"
#blackgrey="\[\033[30;47m\]"
_red="\[\033[31;49m\]"
#green="\[\033[32;49m\]"
#yellow="\[\033[33;49m\]"
_blue="\[\033[34;49m\]"
#magenta="\[\033[35;49m\]"
#cyan="\[\033[36;49m\]"
#white="\[\033[37;49m\]"
r_color="\[\033[0m\]"           # Reset color
#clr="\[\033[K\]"                # Clear to the end of the line

# global test for UID
if [ ${UID} -eq 0 ]; then ## If root is logged in, do something
    user="$_blue\u"
else
    user="$_red\u" ## root isn't logged in, so do something else
fi

## above statement returns the apropriate color for root / someone else        
PS1="$user[\w]$r_color "
unset user r_color _red _blue  ## clear variables

```
If you include the snippet above to your global definition, this will more likely do what you want.

> 
[COLOR="Red"]docter[~][/COLOR] whoami;pwd
docter
/home/docter
[COLOR="Red"]docter[~][/COLOR] su -l
Password: 
[color=blue]root[~][/color] whoami;pwd
root
/root
[color=blue]root[~] [/color]


---

### Post by JKyleOKC on 2009-07-06
About the "empty" question: The "$" prefix of "$BASH" means "return the following environment variable as a string" so if BASH = OkayBoss then $BASH will be "OkayBoss" but if BASH = "" or does not exist then $BASH will be "" (a string of no characters, or empty). Does this help? In my system, $BASH returns "/bin/bash" or the path to the bash program file. If bash were not running, BASH would not exist and thus $BASH would return "".

The reply that says the $BASH test is meaningless is incorrect. In order to "simplify" things, and make a bash script look more like conventional programming languages, some of its "keywords" are single characters rather than being actual words. You've already met "." meaning "source the file given as the argument" and "[" and "]" are others. The "[" character means "test the following argument" while "]" does nothing and is defined simply to provide visual symmetry. Check out the bash tutorials referenced earlier for more details; I don't remember offhand all of the info about "[" and its meaning; as used in this example, it's testing for a non-zero number of characters in the argument.

It looks as if you've got a pretty good grasp of the nesting situation. Remember that the statements between "then" and "else" (or "fi" if no "else" is present) are executed ONLY if the argument tests out as "true" and are totally ignored if the argument returns "false." Similarly, those between "else" and "fi" are executed only if the test returns "false" and are ignored if it's "true."

Keep at it; you're making great progress!

---

### Post by Lostin60's on 2009-07-06
Hello all.  I continue to be amazed by the feedback I keep getting.  In many ways it is better than being in a classroom.  I guess by now you have figured out that I don't quote entire posts.  This is because my posts are usually quite long, as are the replies I get.  Quoting only the relevant lines saves space and makes for easier reading.

@>>>loomsen
I think, sir, that you may be crediting me with more proficiency than I actually have.  I am very new to Ubuntu. I am just starting to learn about bash, and I plan on working on C++ and Pearl.  Years ago I had a few semesters of Pascal and COBAL, which is why I have some knowledge of syntax.  But trust me, I am a babe-in-the-woods here.  As such, there are times when my meaning isn't as clear as it should be.  Now, having clarified that, here I go.

> Your trying to test statements which don't have anything to do with each other.
 Actually, I thought that the .bashrc file was doing that, and I was seeking clarification as to how it could do that, and not hang.```
if [ -f /etc/bash.bashrc ]; then
      . /etc/bash.bashrc 
fi
```  This I understood.  My issue was how it could work in nested conditional statements, as it didn't answer any arguments in the nest.  But that is becoming a bit more clear.  It is a mixed blessing that in most of the replies I get, the posters use the terminology as if I knew it.  This is good, as it pushes me toward learning the jargon.  Sometimes, though, it makes me post, seeking clarification of a term.  All-in-all, though, I much prefer it that way.  "Argument", for instance.  Without having some idea of what that means a lot of what I read would be meaningless to me.  Then there's the usage of a term, and does it mean the same thing in every instance.  But I am getting there.

The bottom line is, I appreciate your post, and although I am really hazy on some of it now, there is a lot that will be very helpful, once I have a grasp of it


@>>>JKyleOKC

I wonder if there will ever come a day when your answer doesn't raise another question.:lol:

> About the "empty" question: The "$" prefix of "$BASH" means "return the following environment variable as a string" so if BASH = OkayBoss then $BASH will be "OkayBoss" but if BASH = "" or does not exist then $BASH will be "" (a string of no characters, or empty). Does this help? Kinda sorta, until > In my system, $BASH returns "/bin/bash" or the path to the bash program file. If bash were not running, BASH would not exist and thus $BASH would return "". This is a good example of what I said to loomsen.

Environment is simply the "set of commands" I am working under.  I can be working in more environments than one.  For instance whatever I do, I am doing it in a BASH environment. If I open Anjuta I am working in a C++ development environment, but also still in a BASH environment.  Is that about right?  If so, where does the concept end.  If I open Open Office Writer.  I assume I am not in a "written media" environment.

The "$" prefix of BASH.  Does it only act on environmental variables, or on any variable?  And what would the distinction between the two be?  Why/how is BASH a variable.  I can understand how SHELL (if it exists) would be a variable, as there are several different shells.  But there is only one BASH. "$" *returns*....  To whom? or to what.  Would return to user need an ECHO command?  Would return to sender need an audio program??(sorry, couldn't resist)  

If it returns to the routine or ?sub-routine? that issues the command, does that automatically answer the argument?  If so, in the .bashrc file (hmm..OK, I am going to assume that PS1 is not "A" prompt, but rather "THE" prompt) then "if [ "$PS1" ]" is a question,(does a prompt exist)or maybe(does a prompt exist or will the code to create a prompt be forthcoming in this routine?) an answer(true/false), and a command(give me the string) all in one. In other words it satisfies itself, and the o/s will go on to the next line of code.  So the o/s will read ```
if [ "$BASH" ]; then

    PS1='\u@\h:\w\$ '
``` and consider it answered, and read the next line. If the next line is "else" the o/s will continue the statement.  If the next line is "fi" the o/s will close the statement.  But if the o/s considers the argument to be answered, even if the statement is not closed it will read the next line with no expectations.  So it will accept an unrelated conditional statement without issue, so long as that statement closes BEFORE the o/s reads a line relating to the previous or original statement.

I think I have that right, or very close to right.  And that would be the reason that ```
if [ -f /etc/bash.bashrc ]; then

	. /etc/bash.bashrc 
    fi

``` is allowed.
 To me, that really shows the importance of "little things."  I was quite concerned with not understanding how that particular piece of code could execute.  It was a "big thing"  Conditional statements in general are a "big thing"  What you said about> The "$" prefix of "$BASH" means "return the following environment variable as a string" is a "little thing"  But that "little thing" led to me understanding my issue with the conditional statement.  Well, understanding it well enough to be comfortable with what I now know.

One last thing> In order to "simplify" things, and make a bash script look more like conventional programming languages, some of its "keywords" are single characters rather than being actual words. You've already met "." meaning "source the file given as the argument" and "[" and "]" are others. The "[" character means "test the following argument" while "]" does nothing and is defined simply to provide visual symmetry. Check out the bash tutorials referenced earlier for more details; I don't remember offhand all of the info about "[" and its meaning; as used in this example, it's testing for a non-zero number of characters in the argument.
 I REALLY understand that, and it has given me no end of grief. I have googled, and checked out several forums with no luck.  I want to find a list of things, and what they mean or their usage like "." and "`" and the difference between 's and "s and "\" and "/"...well you get the idea.

In the tuts, none of that seems to get referenced until the chapter that first uses it. A list of things like IF, DO, FOR, STDERR, and such I can find.  But the slashes and dots and tilde are another matter altogether.  I'm not trying to get ahead of myself, but if I have an issue I would like to be able to have a notion of what the problem file means before I ask for help.

As always, sincere thanks for all the help! 
Have a pleasant evening all. ):P
[COLOR="White"]aa[/COLOR]

---

### Post by JKyleOKC on 2009-07-06
You made an excellent point about the jargon and the meanings of words! Two in particular that we're using a lot in this thread have very different meanings than usual, and can be adding confusion. These two are "argument" and "environment."

"Argument" as I've been using it (and as it appears in much of the available documentation) is synonymous with "parameter" and when talking about the command line, means the words that follow the command word itself. The blank space character separates the arguments. For example, the command "sudo chmod 777 myfile" consists of the command "sudo" followed by three arguments, which are "chmod," "777," and "myfile." The sudo command, in turn, interprets its first argument as a command to be executed and all that follows it are arguments to that command. Thus in this example the second argument to sudo (777) becomes the first argument to "chmod." The purpose of arguments, in general, is to pass information into the command, and the meaning of each argument depends on the specific command itself. If you need to provide an argument that has spaces within it, such as a filename "This is my file," then you can surround it with quote marks to "hide" the embedded spaces from the shell's parsing routines. Usually you'll use double quotes for this purpose, but single quotes are sometimes needed; they tell the parser to do things a bit differently, and the backward single quote has still another special meaning. However these are more advanced facets of how bash works and are best left for later, when you're more comfortable with the flow of operations. The discussion of the differences takes up a full large chapter in my bash reference book!

When you write of "satisfying an argument" this implies to me that you're interpreting "argument" in its conventional meaning rather than the jargonesque way I've been using it. Nothing wrong with that, but it can be a real confusion factor!

"Environment" has similar problems. As used in this context, it refers to a group of "environment variables" that are set up during your log-in process and are used by the shell itself and also by many programs. It's a convention, but not a requirement, that the names of these variables are in all-uppercase letters. To see most of the group, get to a command prompt and type the command "env" with no arguments. You'll get back a batch of cryptic data, only some of which will make any sense at this point. However "USER" should be familiar, and "PWD" will show you your current working directory (not your password, which one might imply from the spelling). However when I tested the command just now, I didn't see the BASH or PS1 variables at all even though I know they are there and they can be viewed with "echo $BASH" and "echo $PS1" commands.

The only place I've found a full list of the bash keywords and modifiers is the book I mentioned at the start of the thread. There are so many that I've never tried to memorize them all! Some of the on-line tutorials may also have such lists, at least covering the most common ones. This shell is actually an extremely powerful programming language, and many of the keywords and modifiers are things used only in very special situations. That's why I keep the book handy for reference whenever I need more than the extremely basic bash idioms!

I suspect that introducing you to "env" will trigger a whole new flood of questions. Keep asking them. As I said before, you're making great progress -- and I'm enjoying trying to give clear answers. I spent more than 50 years as a professional writer, specializing in tutorials, but I've not made much use of that experience in the past dozen years or so. It's making me feel young again!

---

### Post by capscrew on 2009-07-07
There is a list of bash variables listed [_here_]("http://www.gnu.org/software/bash/manual/bashref.html#Bash-Variables").

You can assign variables from the command line.  Maybe this will help you understand the concept.  If I do this from the CLI:```
me=cappy
```I have assigned the value "cappy" to the variable "me". As an aside, you don't need to use caps for variables, but it is the style for most coders of bash scripts.

So how do we call this variable.  Try this from the CLI```
echo I am $me
```

See how the value of the variable is returned?  

The term echo means display to the stdout (the screen) the following.  But as we can see it expands the variable to its value in the return.

At this point, I feel that you should read the tuts you have.  It will clarify a lot, the questions will be more focused and you will be much farther along.

I agree with JKyleOKC.  This brings up ideas that I haven't thought about in years.  It also points out how hard it is to compose succinct non-ambiguous answers to the simplest of questions.

---

### Post by Lostin60's on 2009-07-07
You know, I was thinking of making a list of my most used sentences when posting to you, and putting them in a file.   That way I could open the file and shade it, so when I need a sentence I could un-shade it and copy and paste the sentence.   Being a slow typist I thought this would help.   Further consideration forced me to abandon this idea, as I realized that the list would only contain: what, why, how, and when. :lolflag:

After reading so many replies from you, I get a strong feeling that if I was using your tuts I would have far less questions.   Maybe not, heheh, but the questions would at least be far different.

A short illustrative story.   I mentioned some COBAL classes.  COBAL1 and COBAL2 were taught by "Barbie and Ken" clones.   She made it hard to concentrate programming, and I imagine he had the same effect on the ladies.   They were also engaged.  I had about 20 years on each of them.  To my shame, I can't for the life of me remember either of their names.   In front of the class I referred to them as "Professor" in private it was first name basis.

They were both very good teachers, but their methods were at opposite poles.   In her class there was VERY little theory, but if you wrote down every thing she put on the black-board, you could simply string it all together and probably have a program that would fetch a passing grade, and never compose a line of code on your own.

In his class, you couldn't get a line of code out of him with instruments of torture.    But he taught theory so well, his explanations just pulled the code out of you.  Between the 2 of them you ended up with a rock-solid foundation, and an excellent understanding of both theory and coding.  AHA!!! his name was Sean. 

The point of the story being, that is the feeling I get from all of you posting in this thread.   For everything I ask, I seem to be getting both theory, and actual practice.   Good teachers make good students, and I get the feeling I will make progress much quicker thanks to all of you.

And now a small brag.  In both of their classes I never got below an A.    And to read my posts, you probably wouldn't believe it, but in her class I bet I didn't ask her 4 questions all semester, and only once did I go to her desk because I couldn't get my program to compile.  It was our final assignment.  We had to write a basic payroll program for a small (50 to 100 workers) company.  More specifically, it would be the routine to actually print the checks.

I decided to write a program that was not only correct enough to compile and run, but one that was complete enough to actually be used by a small company and not crash.    We had only just touched on data verification, and it wasn't expected in our assignments, but I decided it was needed. It was a small program, only about 1000 lines, but concise and well written.  And it wouldn't compile.  I spent 4 or 5 days going over it, and I could NOT find my mistake.  

Finally, with only 3 days left to turn it in, I broke down and took it to her.  She flipped it open to the last page and said, "I know why it won't compile."  I asked how she could know that without looking at the code.  She pointed out that it was a thousand lines long.  And I said that I was aware of that.  So she  explained that we were using a "student" compiler, which would not compile more than 500 lines, and I would have to shorten the program to that.

I told her that I really wanted to turn it in, as is, and wasn't there some way around the 500 line limit.  She said she didn't know of one, but I should talk to Sean.  So I did.  We went over it line by line, and Sean said it looked to him like it would do it's job without crashing.  So he showed me a few things, and how to rearrange some things and we got it down to 500 lines in tact.  I thanked him profusely and started to go.  He stopped me and said, "You do understand that if I saw something in your code that would cause a crash, you would not have gotten any help from me.  You're not my student, and you are doing something that is outside the scope of your class, as is the help I gave you.  But you came to me with a well written program and I thought you deserved a chance to turn it in."

I got an A+  Half way through Sean's class I was sitting up front with him helping to debug the other students programs.  He asked me if I owned a computer, which I didn't.  He owned a small consulting firm and said that if I got a computer, he would throw me all the debugging work I could handle, @ $20.00/hr.  Sadly, personal circumstances caused me to have to quit.  And I have never had the chance to go back.

The point of all that is I am not a genius.  The grades came from having excellent professors and a love of what I was doing.  Current circumstances have closed a LOT of doors to me, but have given me the time to do what I love to do, and I am taking full advantage of it.

So, now you have a bit of insight about me. Yes, "env" brought a question or two to mind, most of which can wait a bit.  You also clarified "environment" quite nicely.  So when they call Ajunta a "development environment" they are using environment in a more conventional sense?  Also, when I say jargon I am using it in it's true sense: the technical terminology or characteristic idiom of a special activity or group. In reference to a the command line "argument" and "parameter" are synonymous and define the boundaries in which a command can operate.  Also a cli **must** have an argument to ?regulate? it.  In the manner of "this is what I want you to do(command), and this is how I want it done(argument).  Is parameter the more correct term in this context?   Capscrew, your examples were quite helpful, and bring up a few more questions.  However, I agree it's time to start the tuts.

The one thing neither of you addressed: was I correct in my assessment of why the the .bash_alias "if/then" was allowed in the nested statements.  I have a couple terms I am going to look into, and hit the tuts.  Might be a couple days before I get back to this thread, 2 at most.  As always, I truly do appreciate all that everyone is doing for me. See you all soon.):P

BTW, Jim, let me know when I have you down to 21 and I will ease up on the questions.
[COLOR="White"][/COLOR]

---

### Post by JKyleOKC on 2009-07-08
> **Lostin60's said:**
> So when they call Ajunta a "development environment" they are using environment in a more conventional sense?  Also, when I say jargon I am using it in it's true sense: the technical terminology or characteristic idiom of a special activity or group. In reference to a the command line "argument" and "parameter" are synonymous and define the boundaries in which a command can operate.  Also a cli **must** have an argument to ?regulate? it.  In the manner of "this is what I want you to do(command), and this is how I want it done(argument).  Is parameter the more correct term in this context?

The one thing neither of you addressed: was I correct in my assessment of why the the .bash_alias "if/then" was allowed in the nested statements.  I have a couple terms I am going to look into, and hit the tuts.  Might be a couple days before I get back to this thread, 2 at most.

BTW, Jim, let me know when I have you down to 21 and I will ease up on the questions.

Well, "environment" has several different meanings, even within our jargon (and I too am using "jargon" in its technical sense). A "development environment" usually refers to a program or system of programs which make software development a bit simpler by automating as much of the "drudge work" as possible -- but "KDE," the defining difference for Kubuntu as distinct from Ubuntu or the other *buntu distributions, stands for "Kool Development Environment" which includes the window manager, file manager, and most everything else that defines how you communicate with the underlying operating system! Consistency has never been a strong point in the software world; too many of us suffer from the "not invented here" syndrome...

And no, not all commands require arguments or parameters. The "env" command is one example of such! Many, if not most, do, however. The "echo" command is meaningless without at least one argument telling it what to echo. And whether "argument" or "parameter" is more correct in this context is a matter of opinion; my own opinion is that either is equally correct.

I think you were pretty close in your analysis. As you work through the tutorials you'll see more of the minor details...

You've got a long way to go to get me down to 21; I hesitate to mention my actual age in a crowd with so many youngsters (i.e. those under 65) in it but mentally I hope to stay in middle age forever...

---

### Post by Lostin60's on 2009-07-08
> And no, not all commands require arguments or parameters. The "env" command is one example of such!   The "dir" command would be another.  But if one comes at this question from another direction, could they not be looked at in the manner of "$PS1"?  That is, a command which essentially is "self fulfilling" due to what the command *means*.  Could one not look at "env" as an "ls" command with the argument "all of the environmental variables"? 

You may notice that most of my "what yada yada" questions are usually followed by a "why/how yada yada" question.  I feel that knowing "what" without knowing "why/how" is almost like knowing nothing about "yada yada".  I use to drive my geometry teacher up the wall from hammering him for an explanation of "why" the 5 postulates were true.  To which the only answer is "you just have to take it on faith"  Who says science and religion have nothing in common??
> You've got a long way to go to get me down to 21Heheh...You, sir, have obviously underestimated the depth of my question pool.
[COLOR="White"]aa[/COLOR]

---

### Post by JKyleOKC on 2009-07-08
> **Lostin60's said:**
> Could one not look at "env" as an "ls" command with the argument "all of the environmental variables"? 

Who says science and religion have nothing in common??

Heheh...You, sir, have obviously underestimated the depth of my question pool.

Actually that's an excellent observation: you've assumed a default argument that would apply in the absence of any stated ones. I don't know whether that's what actually happens inside the bash program, or not, but it's a perfect structure for understanding what's going on.

So far as taking things on faith, you do realize that I'm taking it on faith that you exist, and vice versa? Long ago the late lamented CompuServe service, a precursor to the web and forums such as this (where I was a sysop for 15 years), published an ad which was a full-page photo of a cat at a keyboard staring intently at the screen, and the headline "On CompuServe, nobody knows who you really are." It's still true if you substitute "the Internet" for "CompuServe"...

Keep at it. I wouldn't mind being 75 again, anyway!:lolflag:

---

### Post by capscrew on 2009-07-08
> **Lostin60's said:**
> The "dir" command would be another. 
Just to keep things straight; "dir" is an alias for the command "ls -l".> 
But if one comes at this question from another direction, could they not be looked at in the manner of "$PS1"?  
This doesn't quite work out.  The term "ls -l" is a verb in the command sentence "list all in the directory...(in the log form)".  If no specific directory is stated it is inferred that we mean the current directory we are in (as in pwd).  On the other hand $PS1 is NOT a verb in any command sentence.  It is a variable stored in RAM.  this can be looked at programmaticly as an array (or hash).> 
That is, a command which essentially is "self fulfilling" due to what the command *means*.  Could one not look at "env" as an "ls" command with the argument "all of the environmental variables"? 
I would look at commands as the verb in the sentence you are constructing, be it in a script or at the command line.  > 

You may notice that most of my "what yada yada" questions are usually followed by a "why/how yada yada" question.  I feel that knowing "what" without knowing "why/how" is almost like knowing nothing about "yada yada".  I use to drive my geometry teacher up the wall from hammering him for an explanation of "why" the 5 postulates were true.  To which the only answer is "you just have to take it on faith"  Who says science and religion have nothing in common??
Heheh...You, sir, have obviously underestimated the depth of my question pool.
[COLOR="White"]aa[/COLOR]

---

### Post by Lostin60's on 2009-07-09
@>>> capscrew
> Just to keep things straight; "dir" is an alias for the command "ls -l". Is it really?  I didn't know that, but it does typify what I was saying..or at least what I meant.  I realize they are not always one and the same, but I'm working on it.  Out of curiosity, where is the file that "dir" sources?

> On the other hand $PS1 is NOT a verb in any command sentence. It is a variable stored in RAM. this can be looked at programmaticly as an array (or hash).  Array and hash are things I will get to later, I think I have enough food for thought to last awhile. I will, however, make note of that.  In that post I was mostly playing "devil's advocate" to Jim's statement about commands that don't have an argument. I did pick "$PS1" for a reason.  It was a "why" thing.  I know that in nested conditional statements all statements after the first "if" must satisfy a condition of the previous statement.   The second "if" statement  satisfies the first and the 3rd satisfies the second. So no matter how "deep" the nest is all the statements are leading to satisfying the first. 

The .bash statement was completely unrelated. So why did it work? Since it wasn't a Postulate, I knew there had to be an answer..heheh.  Since the "$" in "$PS1" means "return the value of 'PS1'" it is, verb or not, for all intents and purposes, a command to which the argument is "PS1" and the return of the value satisfies the argument. 

I have to assume that somewhere upstream there is a file or routine that looks at it that way.  If not, I am back to "why doesn't the program/routine/file terminate at that point.  Oh, I am speaking of the /etc/profile file.

@>>>JKyleOKC

> Actually that's an excellent observation: you've assumed a default argument that would apply in the absence of any stated ones. I don't know whether that's what actually happens inside the bash program, or not, but it's a perfect structure for understanding what's going on.
 Thank you sir.  Considering the source, I take that as high praise.  And, yes, that was totally an exercise in finding a way to grok the situation. (In a strictly V.M.S. manner)
> The "$" prefix of "$BASH" means "return the following environment variable as a string" THAT is what put me on the track.  When I first saw that I assumed it was just a piece of information that, while useful, was not directly related to my question.  An aside, if you will. 

Now, I wonder.  *Was* it an aside, or did you tell me a "what" to see if I could get at the "how and why of it" on my own? If so....then you are a devious old man!:lolflag::lol:=D>

> Long ago the late lamented CompuServe service, a precursor to the web and forums such as this (where I was a sysop for 15 years), published an ad which was a full-page photo of a cat at a keyboard staring intently at the screen, and the headline "On CompuServe, nobody knows who you really are." I remember the ad well.  I got chuckle out of it.  Excellent advertising too, in the strata of the "Avis.. we try harder" campaign.  I also remember Rush Limbaugh doing his part to keep it afloat..lol.

Referring to something else you said, Keeping your mind middle-aged is **not** going to be an issue.  While I appreciate the content of your posts, I also enjoy the presentation.  I'll bet you tell great "back in the day" stories.):P

---

### Post by capscrew on 2009-07-10
> **Lostin60's said:**
> @>>> capscrew
 Is it really?  I didn't know that, but it does typify what I was saying..or at least what I meant.  I realize they are not always one and the same, but I'm working on it.  Out of curiosity, where is the file that "dir" sources?
All aliases are "sourced" at one time from either bash.bashrc or .profile or .bashrc or .bash_aliases.  The term "dir" as an alias doesn't source anything.  Now that being said, I have to backup on myself and say that the *_command_* "dir" has now been written and **no alias "dir" **is needed.  It still exists though.  See this from my .bashrc file```
# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ] && [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'

    #alias grep='grep --color=auto'
    #alias fgrep='fgrep --color=auto'
    #alias egrep='egrep --color=auto'
fi

```> 

Array and hash are things I will get to later, I think I have enough food for thought to last awhile. I will, however, make note of that.  In that post I was mostly playing "devil's advocate" to Jim's statement about commands that don't have an argument. 
If not clearly stated then they are implied.  > 

... Since the "$" in "$PS1" means "return the value of 'PS1'" it is, verb or not, for all intents and purposes, a command to which the argument is "PS1" and the return of the value satisfies the argument.

The $ in PS1 does not literally mean "return the value of 'PS1'".  Jim was stating it in a practical matter.  The $PS1 is a variable and the $ is what makes it a variable to the command line interpreter. When the interpreter parses the $VARIABLE it looks to the place pointed to in RAM where the $VARIABLE data is stored and returns it.  Remember how the variable was preceded by "echo" in my demonstration?  Echo is the command and $VARIABLE is  the data.

There is one other time you will see $VARIABLE used in a script.  When you assign data to it!  As in: ```
$VARIABLE=data
```

This can be in a conditional statement (if), as in if <something exists> assign this data to the variable.

> I have to assume that somewhere upstream there is a file or routine that looks at it that way.  If not, I am back to "why doesn't the program/routine/file terminate at that point.  Oh, I am speaking of the /etc/profile file.

Because you are assigning data to the variable only.  nothing need be returned.

---

### Post by dromichaetes on 2009-07-10
> **capscrew said:**
> If not clearly stated then they are implied.  The $ in PS1 does not literally mean "return the value of 'PS1'".  Jim was stating it in a practical matter.  The $PS1 is a variable and the $ is what makes it a variable to the command line interpreter. When the interpreter parses the $VARIABLE it looks to the place pointed to in RAM where the $VARIABLE data is stored and returns it.  Remember how the variable was preceded by "echo" in my demonstration?  Echo is the command and $VARIABLE is  the data.

There is one other time you will see $VARIABLE used in a script.  When you assign data to it!  As in: ```
$VARIABLE=data
```

Capscrew, very good explanation. 

Lostin'60, I am as you at the beginning of learning **to understand correctly **bash. And I can tell you from my own experience that you will be well advised to refer to a bash-tutorial, because it will explain you a lot of things which now may appear fuzzy. For instance, I am using right now a tutorial which comes with exercises and which I wholeheartedly recommend to you: [link here]("http://linuxreviews.org/beginner/Bash-Beginners-Guide/en/index.html") . You will find in here more information about [variables]("http://linuxreviews.org/beginner/Bash-Beginners-Guide/en/x1458.html"), [quoting characters]("http://linuxreviews.org/beginner/Bash-Beginners-Guide/en/x1984.html"), and [shell expansion]("http://linuxreviews.org/beginner/Bash-Beginners-Guide/en/x2048.html").

On the other hand, I had [my own questions]("http://ubuntuforums.org/showthread.php?t=1208354") concerning the variable $PS1. But I think it is more a matter of not fully being able to cope with the bash language yet.

---

### Post by JKyleOKC on 2009-07-10
> **Lostin60's said:**
> THAT is what put me on the track.  When I first saw that I assumed it was just a piece of information that, while useful, was not directly related to my question.  An aside, if you will. 

Now, I wonder.  *Was* it an aside, or did you tell me a "what" to see if I could get at the "how and why of it" on my own? If so....then you are a devious old man!

Referring to something else you said, Keeping your mind middle-aged is **not** going to be an issue.  While I appreciate the content of your posts, I also enjoy the presentation.  I'll bet you tell great "back in the day" stories."Experience and cunning always overcome youth and enthusiasm" is one of my favorite proverbs even though it's not always accurate...

I try to avoid "back in the day" stories and never say "get off my lawn" (both actions as part of keeping my mind younger than my body) but I will say it was fun to be part of the vanguard back in the 60s and 70s, when I was hired to write the service manuals for the very first raster-based video terminal, and learned software by trial and error, after working hours...

A few of us from the old CompuServe CLMFORUM community are still on line in a semi-private newsgroup we call The Pub, where we swap tales of the early days and commentary on how things are going.

---

### Post by Lostin60's on 2009-07-11
@>>> capscrew

Hmm, I think I follow you.  But first I may have mis-spoke.  > I know that in nested conditional statements all statements after the first "if" must satisfy a condition of the previous statement. The second "if" statement satisfies the first and the 3rd satisfies the second. So no matter how "deep" the nest is all the statements are leading to satisfying the first.  This is true in COBAL, but might not be in other languages.  If that is not the case in BASH, then my initial question of why the /ect/profile file did not cause a crash is invalid, as it presupposed the quoted statement to be true.

So, let's see if I am understanding you correctly. PS1 is a variable for "prompt", and you and I know that when we see it. However, for the Command line Interpreter to recognize it as such it needs to be prefaced with $.  So that $PS1 just says "Hey, Command line Interpreter($), the following(PS1) is a variable."  To facilitate understanding of my meaning (parse=read), although it means more. To use your "sentence" analogy $ would be an adjective to the noun(pro-noun?) PS1.  So there is no verb. So far I am with you. But it raises a question. Or two.```
if [ "$PS1" ]; then
  if [ "$BASH" ]; then                       
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi
``` Since we have been discussing the above, I will use it as an example.  From what you explained I think that```
if [ "$PS1" ]; then
fi
``` would be a complete if/then statement.  However, being a sentence with no verb, it wouldn't DO anything. My question would be: Is it a *function* of the Command line Interpreter, to automatically seek out a variable and hmm..flip a true/false switch, when it reads $VARIABLE ?  

```
if [ "$BASH" ]; then                       
    PS1='\u@\h:\w\$ '
``` How is (PS1='\u@\h:\w\$) handled? If strings are read verbatim, then, for instance, "for" would be read as the *word* for rather than the *command* for. So how does ('\u@\h:\w\$) get outputted to my screen as "daniel@mypos:~$) ?  Is there something somewhere that basically says(forgive my attempt at coding this) ```
if   [ $BASH  ] ;  then
	get [$username] ;  
	get [$computername] ; for
	 	'PS1='\u@\h:\w\$'
			username= 'u'
			computername= 'h' 
			~= 'w';
	for
		'PS1='\u@\h:\w\$'
	echo \u@\h:\w\$
fi
	 
```

I await your reply.  As always, thanks to all!

Almost forgot,
@>>> dromichaetes

Looks like a great tut, I appreciate the info!
[COLOR="White"]aa[/COLOR]

---

### Post by JKyleOKC on 2009-07-11
Would it help any for me to translate that bit of code from "bash" to English? Here's what I think it would be:
```

if variable PS1 hasn't yet been defined then
  if running under bash then                       
    set value of PS1 to '\u@\h:\w\$ '
    and also if file /etc/bash.bashrc exists then
	source /etc/bash.bashrc (execute it as if it were here)
    end of test for file existing
  else if not running under bash then
    if verb "id" modifier "-u" returns 0 (logged in as root) then
      set value of PS1 to '# '
    else if it returns anything else
      set value of PS1 to '$ '
    end of test for id value
  end of test for running under bash
end of test for value of PS1

```
and that first "set value of PS1" introduces the subject of "escape sequences" which are features of the parsers for bash and most if not all other shells: The backslash character tells the parser to interpret the next character as an abbreviation for something else. Thus "\u" is interpreted as the username of the logged-in user, "\h" is the name of the host system, "\w" is the current working directory, and "\$" is a sequence which may be unique to bash and means "#" if the user id is 0 or "$" otherwise (that is, it encapsulates the entire "not running under bash" branch of our if statement).

Consequently the outcome of this entire block of code is to set the prompt to "username@host:current_directory(# or $)" if running under bash, or just "(# or $)" otherwise, but do this only the first time the program is run after logging in and after that don't change it if the program runs again. The program will run each time a script executes, which is what makes the first-time test necessary.

Does this help any, or does it just raise new questions?

---

### Post by capscrew on 2009-07-12
> **Lostin60's said:**
> @>>> capscrew

Hmm, I think I follow you.  But first I may have mis-spoke.
> know that in nested conditional statements all statements after the first "if" must satisfy a condition of the previous statement. The second "if" statement satisfies the first and the 3rd satisfies the second. So no matter how "deep" the nest is all the statements are leading to satisfying the first.

This is true in COBAL, but might not be in other languages.  If that is not the case in BASH, then my initial question of why the /ect/profile file did not cause a crash is invalid, as it presupposed the quoted statement to be true.
At this point we are basically *"contemplating our own belly button lint"*, as my wife puts it.  But her goes the explanation anyway.  :D  The bash interpreter works as follows (from the bash man pages):```
[COLOR="Blue"]**if list; then list; [ elif list; then list; ] ... [ else list; ] fi**[/COLOR]
              The  if  list is executed.  If its exit status is zero, the then
              list is executed.  Otherwise, each  elif  list  is  executed  in
              turn,  and  if  its  exit status is zero, the corresponding then
              list is executed and the command completes.  Otherwise, the else
              list  is executed, if present.  The exit status is the exit sta&#8208;
              tus of the last command executed, or zero if no condition tested
              true.

```To my way of thinking the following is most pertinent ```
"If its exit status is zero, the the list is executed.  

Otherwise, each  elif  list  is  executed  in turn...
```  This is appears to be counter to your COBAL notion where **ALL** if conditions need to be 0 (true).  I looked at the COBAL conditional if statements.  It looks as if they are like bash, but I am no expert in COBAL.

I don't see anything special so far as being nested.
> 

So, let's see if I am understanding you correctly. PS1 is a variable for "prompt", and you and I know that when we see it. However, for the Command line Interpreter to recognize it as such it needs to be prefaced with $.  So that $PS1 just says "Hey, Command line Interpreter($), the following(PS1) is a variable."  To facilitate understanding of my meaning (parse=read), although it means more. To use your "sentence" analogy $ would be an adjective to the noun(pro-noun?) PS1.  So there is no verb. So far I am with you. But it raises a question. Or two.```
if [ "$PS1" ]; then
  if [ "$BASH" ]; then                       
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi
``` Since we have been discussing the above, I will use it as an example.  From what you explained I think that```
if ; then
fi
``` would be a complete if/then statement.  However, being a sentence with no verb, it wouldn't DO anything.
I think you are better served if you think of it as a test for rest of the sentence i.e. if this $VAR tests true; then do this [Implied -- if not, do this].   I would also note that we humans can (and do) write bad code that will cause the interpreter to return errors! > 

 My question would be: Is it a *function* of the Command line Interpreter, to automatically seek out a variable and hmm..flip a true/false switch, when it reads $VARIABLE ?  

In a word; no.  Variables are used in other instances too.  Our discussion is on the use of the conditional if.  The variable is just what we are testing the condition of (true or false).  As an example we could test the existence of a file in a directory.  The if conditional is just a logical test (yes/no - true/false -- exists or not)

---

### Post by Lostin60's on 2009-07-13
@>>>capscrew

> This is appears to be counter to your COBAL notion where ALL if conditions need to be 0 (true). I looked at the COBAL conditional if statements. It looks as if they are like bash, but I am no expert in COBAL. Well, it has been 25 yrs or so, I may be misremembering. Or maybe it was just coincidence that mine all turned out that way.> At this point we are basically "contemplating our own belly button lint", Yeah...well I have been know to succumb to the "tempest in a tea-pot syndrome occasionally.  But I do have a better handle on it now.  At least I see the errors in how I looked at the statement as a whole. 


@>>> JKyleOKC

> if variable PS1 hasn't yet been defined then  And therein is where I met my Waterloo.```
if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi

```  While I was thinking it to be unrelated, it is in fact the crux of the set of if/thens.  And just think, it only took the two of you 4 or 5 days to get that idea across to me. Sometimes I worry about me. Sigh...  I have, however, got it straight now.

I just want the two of you to know that I really appreciate the effort you put into getting me to understand.  But don't worry, I am sure I will find another dead horse to beat in the near future.  ):P
[COLOR="White"]aa[/COLOR]

---

