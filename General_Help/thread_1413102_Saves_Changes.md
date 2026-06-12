---
title: "Saves Changes"
date: 2010-02-22
forum: General Help
---

### Post by daniel50096230 on 2010-02-22
I had make changes on the following text in Ubuntu terminal, how can I save the changes and go back to the main command?

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /home/support/sohai
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/support/sohai/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

-- INSERT --                                                  1,8           Top

---

### Post by darolu on 2010-02-22
What program did you use to edit your text?

Well, for the -- INSERT -- line at the bottom, I assume you used Vi or Vim; to save and exit, first press ESC to enter command mode and then type ":wq" (write quit).

Read this link to learn more: [http://vimdoc.sourceforge.net/htmldoc/usr_toc.html](http://vimdoc.sourceforge.net/htmldoc/usr_toc.html)

---

