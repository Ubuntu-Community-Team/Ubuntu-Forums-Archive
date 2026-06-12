---
title: "Problem with Plone 3"
date: 2010-08-10
forum: General Help
---

### Post by _khAttAm_ on 2010-08-10
I installed Plone 3.3.5 on my Ubuntu 10.10 Maverick Meerkat 64bit Desktop with Plone Unified Installer - for Linux/BSD/OS X/UNIX/Solaris. The installation was successful.

Then I ran the instance of Zope by changing directory to where my Plone is installed and running the following in terminal:
```
sudo ./bin/instance fg
```
Then I could browse the url [http://localhost:8888/manage](http://localhost:8888/manage) (I had changed the port number to 8888 ). 

However, when I tried to create a Plone Site using Zope interface, I got the following error:
> Site Error

An error was encountered while publishing this resource.

Error Type: KeyError
Error Value: ''

I see the following error in the terminal:
>   Module DateTime.DateTime, line 1145, in toZone
KeyError: ''
Unhandled exception in thread started by <class ZServer.PubCore.ZServerPublisher.ZServerPublisher at 0x7f5634b1f110>
Traceback (most recent call last):
  File "/usr/local/Plone/Zope-2.10.11-final-py2.4/lib/python/ZServer/PubCore/ZServerPublisher.py", line 25, in __init__
    response=b)
  File "/usr/local/Plone/Zope-2.10.11-final-py2.4/lib/python/ZPublisher/Publish.py", line 401, in publish_module
    environ, debug, request, response)
  File "/usr/local/Plone/Zope-2.10.11-final-py2.4/lib/python/ZPublisher/Publish.py", line 227, in publish_module_standard
    if request is not None: request.close()
  File "/usr/local/Plone/Zope-2.10.11-final-py2.4/lib/python/ZPublisher/BaseRequest.py", line 211, in close
    notify(EndRequestEvent(None, self))
  File "/usr/local/Plone/Zope-2.10.11-final-py2.4/lib/python/zope/event/__init__.py", line 23, in notify
    subscriber(event)
  File "/usr/local/Plone/Zope-2.10.11-final-py2.4/lib/python/zope/component/event.py", line 26, in dispatch
    for ignored in zope.component.subscribers(event, None):
  File "/usr/local/Plone/Zope-2.10.11-final-py2.4/lib/python/zope/component/_api.py", line 130, in subscribers
    return sitemanager.subscribers(objects, interface)
  File "/usr/local/Plone/Zope-2.10.11-final-py2.4/lib/python/zope/component/registry.py", line 290, in subscribers
    return self.adapters.subscribers(objects, provided)
AttributeError: adapters

I tried adding the following in buildout.cfg under *instance* section:
```
zope-conf-additional =
    <environment>
        TZ Asia/Katmandu
    </environment>
```
as instructed [here]("http://bibekpaudel.wordpress.com/2009/11/26/solved-plone-installation-strange-error/") and running buildout again but this did not work for me as I got the same error again.

I then installed Ubuntu 10.04 Lucid Lynx 32bit Server in Virtualbox and installed Plone again. This time I used Python 2.4 from Hardy repos rather than having it built by Plone installer. I used the tutorial [here]("http://plone.org/documentation/kb/installing-a-plone-buildout-on-ubuntu") for rest of the stuff. But the same error again.

Has anyone managed to solve this issue? Any help will be appreciated. Thanks.

UPDATE: I installed the same in CentOS 5.5 and got the exact same error. I guess I'm doing something gravely wrong here. Please help out.

UPDATE: [Additional Details and workaround here.]("http://www.khattam.info/solved-module-datetime-datetime-line-1145-in-tozone-2010-08-19.html")

---

