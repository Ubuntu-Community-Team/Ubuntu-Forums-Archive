---
title: "environment variables: &quot;command not found&quot;"
date: 2011-02-10
forum: General Help
---

### Post by nolsen01 on 2011-02-10
I'm trying to install Grails.

I put the following in /etc/bash.bashrc:

```
JAVA_HOME=/usr/lib/jvm/java-6-openjdk
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH

# # # Groovy
GROOVY_HOME = /usr/share/groovy
export GROOVY_HOME
PATH = $PATH:$GROOVY_HOME/bin
export PATH

# # # Grail
GRAILS_HOME = /usr/share/grails
export GRAILS_HOME
PATH = $PATH:$GRAILS_HOME/bin
export PATH
```

When I startup my terminal, is says:

```
GROOVY_HOME: command not found
PATH: command not found
GRAILS_HOME: command not found
PATH: command not found
```

It has no problems with JAVA_HOME, but for some reason has problems with GRAILS_HOME and GROOVY_HOME.

I've checked over and over again, and sure enough, /usr/share/ contains both a folder called grails *and* a folder called groovy. Also, I have restarted my computer, several times.

Does anybody have any ideas?

---

### Post by AlphaLexman on 2011-02-10
> **nolsen01 said:**
> GROOVY_HOME = /usr/share/groovy
GRAILS_HOME = /usr/share/grails
Should be:```
GROOVY_HOME=/usr/share/groovy
```and```
GRAILS_HOME=/usr/share/grails
```
EDIT: And:
> **nolsen01 said:**
> PATH = $PATH:$GRAILS_HOME/bin
Should be:
```
PATH=$PATH:$GRAILS_HOME/bin
```
NOTICE: the lack of 'spaces' around the equal sign (=)

---

### Post by nolsen01 on 2011-02-10
Awesome. Thank you.

---

