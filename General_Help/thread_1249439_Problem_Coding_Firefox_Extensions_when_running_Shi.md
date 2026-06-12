---
title: "Problem Coding Firefox Extensions when running Shiretoko"
date: 2009-08-25
forum: General Help
---

### Post by nizdobs on 2009-08-25
I'm running Ubuntu 9.04. I upgraded Firefox to 3.5, Shiretoko. I am looking to code a Firefox extension. As part of this process I need to specify a target application id in my install.rdf. I know that for Firefox the target application id is:
{ec8030f7-c20a-464f-9b0e-13a3a9e97384}.

I coded the extension on a Windows box running Firefox 3.5 and the extension ran fine. When I compiled the xpi file on Windows and loaded the xpi file in Shiretoko I saw the desired behavior.

However, if I package the code on Ubuntu and run it on Shiretoko it doesn't display the expected behavior. Given that I went through an identical process that worked in Windows I can't quite figure out why it wouldn't have worked.

My only thought is that perhaps Shiretoko needs a different target application id in install.rdf? Might that be why it's not working?

Thanks for the help.

- Niz

---

