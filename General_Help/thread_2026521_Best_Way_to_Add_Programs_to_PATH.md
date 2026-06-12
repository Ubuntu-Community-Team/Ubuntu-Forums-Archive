---
title: "Best Way to Add Programs to PATH"
date: 2012-07-15
forum: General Help
---

### Post by ajoberstar on 2012-07-15
While I have been using Ubuntu off and on for about 7 years, I have a much stronger Windows background.

When I do Java development I like to have some of my supported tools on the path, but don't always want the versions available in Software Center.  In Windows, I would normally download a tool such as Groovy and unpack the zip into a directory.  Then I would set an environment variable GROOVY_HOME pointing to that new directory and add %GROOVY_HOME% to my path.

I have tried using ~/.profile (which I have gotten to work) and ~/.pam_environment which hosed up my PATH.  I'm not necessarily looking for the best way to set an environment variable (or the right way to use .pam_environment).  I'm really looking for the most idiomatic way a Ubuntu user would add a new tool to their user-specific PATH.

One other thing I haven't tried, but seems like it might be the answer is to use ~/bin.  However, unless I'm mistaken, this does mean I need symlinks for every individual shell script in each respective tool's bin directory.  In most cases there are only 1-2 per tool, so that might be fine.

Thoughts?

---

### Post by Cheesemill on 2012-07-15
Just add them at the bottom of your ~/.profile file:
```
export PATH="$PATH:/a/path/to/add:/another/path/to/add:/yet/another/path"
```

---

### Post by ajoberstar on 2012-07-15
> **Cheesemill said:**
> Just add them at the bottom of your ~/.profile file:
```
export PATH="$PATH:/a/path/to/add:/another/path/to/add:/yet/another/path"
```

The reason I avoided ~/.profile was that it was marked not-recommended in the help. They don't explain why it's not recommended though.

[https://help.ubuntu.com/community/EnvironmentVariables#Session-wide_environment_variables](https://help.ubuntu.com/community/EnvironmentVariables#Session-wide_environment_variables)

---

### Post by bab1 on 2012-07-15
> **ajoberstar said:**
> The reason I avoided ~/.profile was that it was marked not-recommended in the help. They don't explain why it's not recommended though.

[https://help.ubuntu.com/community/EnvironmentVariables#Session-wide_environment_variables](https://help.ubuntu.com/community/EnvironmentVariables#Session-wide_environment_variables)

I believe the reason  is because it is not consistent in all set ups (e.g YMMV).  

See 
```
2.  ~/.bash_profile or ~./bash_login - [B][COLOR="Red"]If one of these file exist, 
bash executes it rather than "~/.profile" when it is started 
as a login shell. [/COLOR][/B](Bash will prefer "~/.bash_profile" to "~/.bash_login"). 
However, these files won't influence a graphical session by default. 
```

I assume you are reading from here: [**_[COLOR="Blue"]https://help.ubuntu.com/community/EnvironmentVariables[/COLOR]_**]("https://help.ubuntu.com/community/EnvironmentVariables")

---

### Post by ajoberstar on 2012-07-15
OK, I think that answers my question.  Thanks, guys!

---

