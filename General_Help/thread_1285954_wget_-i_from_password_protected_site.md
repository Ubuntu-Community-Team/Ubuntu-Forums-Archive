---
title: "wget -i from password protected site"
date: 2009-10-08
forum: General Help
---

### Post by krage on 2009-10-08
Hi

I am trying to use wget do download many files from a website that is password protected

From a site with no password protection I would use wget-i dwn.txt 
and then put all the URLs in the dwn.txt file.

But how would I wo this when the files are password protected?

---

### Post by alphaniner on 2009-10-08
You can give a username and password for wget to use, but I don't know if they will work in your situation.  And if you require different credentials for the various sites in the list it definitely won't work.

[quote='man wget']       --user=user
       --password=password
           Specify the username user and password password for both FTP and HTTP file retrieval.  These parameters can be overridden using the --ftp-user and --ftp-password options for FTP connections and the --http-user and --http-password options for HTTP connections.
[/quote]

---

