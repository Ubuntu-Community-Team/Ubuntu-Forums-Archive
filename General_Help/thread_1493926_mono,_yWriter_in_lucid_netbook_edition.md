---
title: "mono, yWriter in lucid netbook edition"
date: 2010-05-26
forum: General Help
---

### Post by tcaptain on 2010-05-26
I'm searched through the forums and I saw some older posts but the solutions don't seem to work in Lucid.

I'm trying to run yWriter5 on my netbook (I love this app) and wine doesn't run it, it requires mono.

However, when I try to run it, I get an error:

'The assembly mscorlib.dll was not found or could not be loaded.'
'It should have been installed in the '/usr/lib/mono/1.0/mscorlib.dll' directory'

After googling and searching the forums, I saw a tidbit I thought I'd try (from an old problem regarding OpenSim) which is basically creating a symlink to /usr/lib/mono/2.0/mscorlib.dll.

Running again, I now get a different error altogether:

'WARNING ***: The following assembly referenced from /home/xxxxx/.wine/drive_c/Program Files/yWriter5/yWriter.exe could not be loaded:
Assembly:  Microsoft.VisualBasic  (assemblyref_index=1)
Version:   8.0.0.0
Public Key: b03f5f7f11d50a3a
The assembly was not found in the Global Assembly Cache, a path listed in the MONO PATH variable, or in the location of the executing assembly'

In other posts, some say to install libmono-microsoft-visualbasic8.0cil but I can't find that package for Lucid.

I'm hoping someone can point me in the right direction?

---

### Post by tcaptain on 2010-05-27
Anyone?

I'd like to add that I'm also having this problem using Lucid on my desktop PC (fresh install) and my full sized laptop (also fresh install)

---

### Post by spaceshipguy on 2010-06-20
Hi I was having the same problem, and on the OpenSim site there is a troubleshooting page  [http://opensimulator.org/wiki/Troubleshooting#The_assembly_mscorlib.dll_was_not_found_or_could_not_be_loaded](http://opensimulator.org/wiki/Troubleshooting#The_assembly_mscorlib.dll_was_not_found_or_could_not_be_loaded) where they give a link for downloading quite a big package (called nant) that includes this missing file.
I downloaded and then ywriter5 worked.

Hope it works for you.

Now I have to work out how to stop the scene dialogue window going screwy the third time it's opened.

---

