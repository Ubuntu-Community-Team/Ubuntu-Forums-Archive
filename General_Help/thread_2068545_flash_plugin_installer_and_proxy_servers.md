---
title: "flash plugin installer and proxy servers"
date: 2012-10-09
forum: General Help
---

### Post by arch0njw on 2012-10-09
This is driving me batty.  I cannot install the flash plugin when I'm behind my proxy.  So I installed it manually.  But the crazy installer thing keeps barking at me about how it wasn't able to run and install properly.

Is there *any way* to shut this up?  Better yet ... is there any way to make it play properly with a proxy?

Thanks,
 Slowly Going Insane

---

### Post by dcstar on 2012-10-10
> **arch0njw said:**
> This is driving me batty.  I cannot install the flash plugin when I'm behind my proxy.  So I installed it manually.  But the crazy installer thing keeps barking at me about how it wasn't able to run and install properly.

Is there *any way* to shut this up?  Better yet ... is there any way to make it play properly with a proxy?

Thanks,
 Slowly Going Insane

Set the Proxy setting correctly in Synaptic so the package can actually download the external files it needs (Flash) and install correctly.

---

### Post by arch0njw on 2013-02-11
> **dcstar said:**
> Set the Proxy setting correctly in Synaptic so the package can actually download the external files it needs (Flash) and install correctly.

I am able to download the packages.  That is not the problem.  The problem is the final part of the flash installer where it is trying to run at this point:

flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.262.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.262.orig.tar.gz)

This, as I have read elsewhere, is not configured in Synaptic.  This is a setting elsewhere that people have intermittently gotten to work.

Help on this would be appreciated so I can get this to work properly.  It would be so nice if this would work with the proxy settings.


Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 234, in process_download_requests
    dest_file = urllib.urlretrieve(files[i])[0]
  File "/usr/lib/python2.7/urllib.py", line 93, in urlretrieve
    return _urlopener.retrieve(url, filename, reporthook, data)
  File "/usr/lib/python2.7/urllib.py", line 239, in retrieve
    fp = self.open(url, data)
  File "/usr/lib/python2.7/urllib.py", line 207, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 344, in open_http
    h.endheaders(data)
  File "/usr/lib/python2.7/httplib.py", line 954, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python2.7/httplib.py", line 814, in _send_output
    self.send(msg)
  File "/usr/lib/python2.7/httplib.py", line 776, in send
    self.connect()
  File "/usr/lib/python2.7/httplib.py", line 757, in connect
    self.timeout, self.source_address)
  File "/usr/lib/python2.7/socket.py", line 571, in create_connection
    raise err
IOError: [Errno socket error] [Errno 110] Connection timed out

---

