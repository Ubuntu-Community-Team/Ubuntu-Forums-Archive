---
title: "Google Chrome pdf handling"
date: 2009-10-10
forum: General Help
---

### Post by gewitty on 2009-10-10
Does anyone know how to change the way that Chrome handles pdf files? At present there doesn't seem to be a plug-in available, so if you click on a pdf link you end up with a black screen. 

Can Chrome be instructed to use an external pdf reader when it encounters these files?

---

### Post by thecow on 2009-10-20
I have the same issue.  When I type about:plugins it shows that I have a pdf handler, so Im not sure what the issue is

---

### Post by j7%&lt;RmUg on 2009-10-20
Are you using the stable chrome or dev chrome? im running the dev chrome and i can open .pdf's fine.

---

### Post by lariosa42 on 2009-10-20
I've had this problem for months.  Despite countless hours of Google searching, I have found absolutely no solution that works for me.  I have heard some people had success by uninstalling and reinstalling Adobe, but I can't count myself among them.

There is also the non-fix of opening Adobe and telling it not to open pdfs in your browser.  I can't find the option (yes, I looked under "Internet" in the preferences), so this hasn't worked for me either.

This is extremely frustrating as I have to read scientific articles every day, and often need to open 20-30 pdfs in a day.  Unfortunately, Firefox is still crashing, so that's not an option either.  Why won't Google fix this?

---

### Post by lariosa42 on 2009-10-20
By the way, I'm using Chromium 4.0.222.1 (Ubuntu build 28248) on Jaunty 9.04.

---

### Post by j7%&lt;RmUg on 2009-10-20
Do you really have to double post? please dont.

---

### Post by lariosa42 on 2009-10-20
nisshh-
My, aren't we vigilant!  It was an accident.  For some reason Chromium froze when I tried to post, I clicked again, and the post went up twice.  I couldn't figure out how to delete the duplicate post, so I edited it to say something I was going to edit into the original post.  

Now, can we get back to the topic?

---

### Post by thecow on 2009-10-20
> **nisshh said:**
> Are you using the stable chrome or dev chrome? im running the dev chrome and i can open .pdf's fine.

What version do you have?  I am running 4.0.222.5  This might be something that they have finally fixed

---

### Post by varsamakos on 2009-10-31
I'm on 4.0.226.0 (Ubuntu build 30050) and I still can't view .pdf files.

&#921; can't find a solution. Pdf plugin is enabled.

Any help would be appreciated.

---

### Post by lilbill on 2009-10-31
I don't know if this helps, but for my Chrome installation on Windows I downloaded a .pdf with Chrome by right-clicking and then told it to always open the file with my favorite .pdf reader.  This opens a new reader window, but if you use something which supports tabs it can be very convenient to open multiple documents at once (I'm a math grad student so I need to do this often)

Also, note that firefox plugins typically work with chrome so that if you take your favorite reader's firefox plugin and put in a 'Plugins' directory in the Chrome folder it will default to this one over those it inherited from firefox.

Hope that helps (I've never used chrome on Linux)

---

### Post by ecoxmit on 2009-11-05
I had this issue with one computer (acrobat plugin worked fine on another). I fixed this issue by removing the acrobat firefox plugin: now chrome does not try to open up the pdf file _within_ the browser itself, just downloads it and you can just click the downloaded file name. 

In your chrome bar, type:

```
about:plugins
```

Look there for the acrobat plugin name (something that ends in .so and contains pdf in its name, can't remember exactly what it was called). Then, in the terminal do
```

$ sudo updatedb
$ locate <plugin name here>

```
and delete the acrobat plugin from all the locations where you see it. 

Restart chrome. That should work. If you want your acrobat firefox plugin back, just reinstall acroread from synaptic.

---

### Post by ecoxmit on 2009-11-05
Also, you might want then to have chrome download the files automatically without asking you for confirmation (you can choose that in the chrome's Options menu)

---

### Post by fshapps on 2009-12-12
I removed Acrobat entirely and now PDFs download like any other file.

---

### Post by motorhead_1 on 2010-02-02
edit

---

### Post by linuxape on 2010-02-10
I was having this same issue with chrome in Ubuntu8.10. Trying to open any PDF within chrome will result in a black page being displayed. However after installing gPDF extension ([https://chrome.google.com/extensions/detail/egljjohbmnnpicoiddaapkpejfpnmmpe](https://chrome.google.com/extensions/detail/egljjohbmnnpicoiddaapkpejfpnmmpe)) from chrome extension library fixed the problem.  You will need to restart the browser for the extension to take effect.  Hope this helps.

---

### Post by dunnerz on 2010-02-17
> **linuxape said:**
> I was having this same issue with chrome in Ubuntu8.10. Trying to open any PDF within chrome will result in a black page being displayed. However after installing gPDF extension ([https://chrome.google.com/extensions/detail/egljjohbmnnpicoiddaapkpejfpnmmpe](https://chrome.google.com/extensions/detail/egljjohbmnnpicoiddaapkpejfpnmmpe)) from chrome extension library fixed the problem.  You will need to restart the browser for the extension to take effect.  Hope this helps.

Nice idea, but when it's google docs producing the PDF (to print) this becomes an issue!

---

### Post by Elktro on 2010-02-23
I have been trying to solve this problem for quite a while and used countless hours trying to fix it. Here are some links that are interesting for those who are having this problem:

[http://www.google.com/support/forum/p/Chrome/thread?tid=5c1079faa28a6a29&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=5c1079faa28a6a29&hl=en)
[http://code.google.com/p/chromium/issues/detail?id=19587](http://code.google.com/p/chromium/issues/detail?id=19587)
[http://code.google.com/p/chromium/issues/detail?id=26320](http://code.google.com/p/chromium/issues/detail?id=26320)

non of which provided solution, though.

I have now switched back to Firefox, because of this. I preferred google chrome for its faster starting and especially faster closing time, which sometimes took with firefox almost a minute. Now I have fixed the slow closing time creating an icon that kills firefox with -9 signal. Talk about fast closing times!

---

### Post by motorhead_1 on 2010-02-23
this solution worked for me:
Hey Karmic guys,
I found a workaround that worked like a charm for me!
It was pointed out by tomasz.chilinsk and refined by setack on the Chromium Issue 19587 ([http://code.google.com/p/chromium/issues/detail?id=19587](http://code.google.com/p/chromium/issues/detail?id=19587)).

To enable Chrome to view PDF files embedded in the browser, become root and follow these steps:

1 - echo 'deb [http://ppa.launchpad.net/setack/stuff/ubuntu](http://ppa.launchpad.net/setack/stuff/ubuntu) karmic main' >> /etc/apt/sources.list
2 - aptitude update
3 - aptitude install mozplugger

That's it! After that, just restart Chrome and you should be able to view PDF files with Acrobat Reader embedded in the browser.

[http://www.google.com/support/forum/p/Chrome/thread?tid=3b53994488e4f44e&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=3b53994488e4f44e&hl=en)

---

### Post by fragos on 2010-02-23
I installed the Google Docs extension and now Google will open PDF files in Chrome. It's very fast and you can still download the PDF if you wish.

---

### Post by leifjonny on 2010-02-24
Docs PDF/PowerPoint Viewer, problem solved

---

### Post by jetpeach on 2010-03-05
i'll second the solution in 
[http://ubuntuforums.org/showpost.php?p=8250562&postcount=11](http://ubuntuforums.org/showpost.php?p=8250562&postcount=11)
where the plugin is simply deleted (or moved to a backup location.) after doing this, chrome nicely downloads the pdf files in all cases tested (including when you can't use save-as because of javascript links that generate the pdf...). i prefer opening the files separate from the browser anyway so am very happy with this solution..

---

### Post by garkhov on 2010-04-28
> **ecoxmit said:**
> I had this issue with one computer (acrobat plugin worked fine on another). I fixed this issue by removing the acrobat firefox plugin: now chrome does not try to open up the pdf file _within_ the browser itself, just downloads it and you can just click the downloaded file name. 

In your chrome bar, type:

```
about:plugins
```

Look there for the acrobat plugin name (something that ends in .so and contains pdf in its name, can't remember exactly what it was called). Then, in the terminal do
```

$ sudo updatedb
$ locate <plugin name here>

```
and delete the acrobat plugin from all the locations where you see it. 

Restart chrome. That should work. If you want your acrobat firefox plugin back, just reinstall acroread from synaptic.

Brilliant - just the solution I was after :)

---

### Post by fragos on 2010-04-28
You should check the Chrome extension Docs PDF/PowerPoint Viewer (by Google) for viewing PDFs. It's very fast and you can still download the PDF if you wish.

---

### Post by Charlotte18 on 2010-05-19
Google's PDF/PowerPoint Viewer works as long as the site is not secure.  It does not work with https sites.

---

### Post by luigi_mb on 2010-05-19
I am running Chrome v6.0.401.1 dev . This is how I managed so far. I installed the Google/Docs extension, _and_ disabled the MozPlugger plugin. Usually Google/Docs works (and works fast). When it does not (on certain https websites) I am given the option to download pdf's.

/luigi

---

### Post by Francewhoa on 2011-02-16
**Following worked for me**

[LIST=1]
[*]Close Chrome
[*]Browse to: home/*/.config/google-chrome/Default/Preferences
Where * is your Ubuntu username
[*]Make a back up copy of the file:  Preferences
[*]Edit the Preferences file with a text editor such as gedit
[*]Find those lines:
     ```
"extensions_to_open": "",
```
[*]Then change it to:
          ```
"extensions_to_open": "pdf:torrent", 
```
[*]Save file and start Chrome again
[/LIST]
Notes

[LIST]
[*]List of file-types should be in quotes and separated by a colon
[*] Google disabled the auto-open pdf feature because they say it's a  security risk. Google said this issue will be fix in the next stable  release. In the meantime it's a pain. Source:
[LIST]
[*][http://news.cnet.com/8301-30685_3-20024520-264.html](http://news.cnet.com/8301-30685_3-20024520-264.html)
[*][http://blogs.pcmag.com/securitywatch/2010/06/google_chrome_to_add_native_pd.php](http://blogs.pcmag.com/securitywatch/2010/06/google_chrome_to_add_native_pd.php)
[/LIST]
[*] This solution might not work with all versions of Chrome
[*] Source for solution: [http://www.chromeplugins.org/google/bugs-vulnerabilities/autoopen-7869.html](http://www.chromeplugins.org/google/bugs-vulnerabilities/autoopen-7869.html)
[/LIST]

---

