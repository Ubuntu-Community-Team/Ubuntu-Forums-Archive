---
title: "Finding packages-&quot;loose ends&quot;: manually installed &amp; not a dependency"
date: 2011-08-28
forum: General Help
---

### Post by lampak on 2011-08-28
Is there a way to obtain a list of packages which were manually installed and are not a dependency for any other installed package? That is those which can be safely removed.

---

### Post by lampak on 2011-08-28
I didn't find any better solution so I've downloaded Synaptic's source code and modified it a bit. 

In the file common/rpackagefilter.cc I've replaced
```
   if (_status & ManualInstalled) {
      if ( !(flags & RPackage::FIsAuto) && 
            (flags & RPackage::FInstalled))
         return true;
   }
```
with
```
   if (_status & ManualInstalled) {
      if ( !(flags & RPackage::FIsAuto) && 
            (flags & RPackage::FInstalled))
      {
         bool nothingDependsOnIt = true;
         for (pkgCache::DepIterator depIt = pkg->package()->RevDependsList(); !depIt.end(); ++depIt)
         {
            if (depIt->Type != pkgCache::Dep::Depends)
               continue;
            if(depIt.TargetPkg()->CurrentState == pkgCache::State::Installed)
            {
               nothingDependsOnIt = false;
               break;
            }
         }
         if (nothingDependsOnIt)
            return true;
      }
   }
```
Now when I use a custom filter with only the "Manual installed" box ticked I get what I wanted. Maybe not the simplest and neatest solution but works.

---

### Post by jerrrys on 2011-08-28
there are also other options

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+unneeded+dependencies&sa=Search&cof=FORID:9#791](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+unneeded+dependencies&sa=Search&cof=FORID:9#791)

---

