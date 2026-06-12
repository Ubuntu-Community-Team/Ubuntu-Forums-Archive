---
title: "Java script works in MS Windows Firefox but not Ubuntu"
date: 2006-04-04
forum: General Help
---

### Post by JimS on 2006-04-04
...

I wish to be able to use the Danish Arkivalieronline
database via my Linux box.
see  [http://www.arkivalieronline.dk/](http://www.arkivalieronline.dk/)

I can access using MS Windows, but not completely
in Ubuntu, using Firefox 1.07, Epiphany, or Opera.
This database contains photocopies of church records
useful for family history studies.
The language is Danish.
I do not code HTML, Java, or other web languages.

When I am in Ubuntu and Firefox I can log in,
but when I select a parish, I can download a file
call  ViewImage.aspx.  I can't get it to execute.

Using Opera seems to do the same.

When I am in Ubuntu and Epiphany I can also log in,
but when I select a parish, I get the following message:

=======================================
        This XML file does not appear to have any style information associated with it. The document tree is shown below.
      
-
	<jnlp spec="1.0+" codebase="http://www.arkivalieronline.dk/LAView">
-
	<information>
<title>LAView Application</title>
<vendor>Statens Arkiver</vendor>
<description>Fremviser til online arkivalier</description>
<description kind="short"/>
</information>
-
	<security>
<all-permissions/>
</security>
-
	<resources>
<j2se version="1.4+" initial-heap-size="64m" max-heap-size="128m"/>
<jar href="LAView.jar"/>
<jar href="axis.jar"/>
<jar href="clibwrapper_jiio.jar"/>
<jar href="commons-discovery-0.2.jar"/>
<jar href="commons-logging-1.0.4.jar"/>
<jar href="jai_core.jar"/>
<jar href="jai_codec.jar"/>
<jar href="jai_imageio.jar"/>
<jar href="jaxrpc.jar"/>
<jar href="log4j-1.2.8.jar"/>
<jar href="saaj.jar"/>
<jar href="wsdl4j-1.5.1.jar"/>
<property name="bog" value="%2fdata%2fkirkeb%c3%b8ger%2f"/>
<property name="opslag" value="C118/B/015/K01-01-A.Tif,C118/B/015/K01-02-A.Tif,C118/B/015/K01-03-A.Tif,C118/B/015/K01-04-A.Tif,C118/B/015/K01-05-A.Tif,C118/B/015/K01-06-A.Tif,C118/B/015/K01-07-A.Tif,C118/B/015/K01-08-A.Tif,C118/B/015/K01-09-A.Tif,C118/B/015/K01-10-A.Tif,C118/B/015/K01-11-A.Tif,C118/B/015/K01-12-A.Tif,C118/B/015/K01-13-A.Tif,C118/B/015/K01-14-A.Tif,C118/B/015/K01-15-A.Tif,C118/B/015/K01-16-A.Tif,C118/B/015/K01-17-A.Tif,C118/B/015/K01-18-A.Tif,C118/B/015/K01-19-A.Tif,C118/B/015/K01-20-A.Tif,C118/B/015/K01-21-A.Tif,C118/B/015/K01-22-A.Tif,C118/B/015/K01-23-A.Tif,C118/B/015/K01-24-A.Tif,C118/B/015/K01-25-A.Tif,C118/B/015/K01-26-A.Tif,C118/B/015/K01-27-A.Tif,C118/B/015/K01-28-A.Tif,C118/B/015/K01-29-A.Tif,C118/B/015/K02-01-A.Tif,C118/B/015/K02-02-A.Tif,C118/B/015/K02-03-A.Tif,C118/B/015/K02-04-A.Tif,C118/B/015/K02-05-A.Tif,C118/B/015/K02-06-A.Tif,C118/B/015/K02-07-A.Tif,C118/B/015/K02-08-A.Tif,C118/B/015/K02-09-A.Tif,C118/B/015/K02-10-A.Tif,C118/B/015/K02-11-A.Tif,C118/B/015/K02-12-A.Tif,C118/B/015/K02-13-A.Tif,C118/B/015/K02-14-A.Tif,C118/B/015/K02-15-A.Tif,C118/B/015/K02-16-A.Tif,C118/B/015/K02-17-A.Tif,C118/B/015/K02-18-A.Tif,C118/B/015/K02-19-A.Tif"/>
<property name="sessionId" value="tsjpsbmgxbdmt2fovtflyq55"/>
<property name="service" value="http://ao.sa.dk/LAView/ImageServer/Service1.asmx"/>
</resources>
<application-desc main-class="dk.sa.ao.LAViewer">
   </application-desc>
</jnlp>
=======================================

In MS Window XP Home and Firefox 1.07 I get a little window
saying "You have chosen to open ViewImage.aspx which is a JNLP
file from [http://www.arkivalieronline.dk](http://www.arkivalieronline.dk).
What should Firefox do with the file?
Open with JNLPFile (default)
Save to Disk
Do this automatically for files like this from now on."
I select "Open with JNLPFile (default), the file downloads, installs, 
and I am in and can look at the parish records.

It would appear that in Ubuntu I may need something that
takes this ViewImage.aspx and executes it.
What could that be????

[COLOR="Red"]JimS[/COLOR]
[COLOR="Blue"]Prostate Cancer Aware[/COLOR]

---

### Post by JimS on 2006-04-14
...

I see that I have had no takers, so I will ask another
question that may apply to my problem.

What java packages might I add from the Synaptic
Package Manager that might allow loading of the
above mentioned "ViewImage.aspx"?

In Synaptic Package Manager I searched on "sun"
and a lot of java stuff came up.  Interesting, but
since I have no expertize in web scripting and java,
I'm lost.

[COLOR="Red"]JimS[/COLOR]

---

### Post by jwalch on 2006-04-28
Had the same problem...found a solution at <http://forums.mozillazine.org/viewtopic.php?t=406306&>

which is:

download the file from the DK site, which will be

ViewImage.aspx

open with javaws  (you have to manually type this, at the far bottom of the list of alternatives) The file then downloads, with the Java app that opens it.

(This is for Firefox, I haven't tried the other browsers)

Jim Walch,
Sollentuna, Sweden
<jimwalch@glocalnet.net>

---

