---
title: "Problems with g++ 4.4"
date: 2010-04-29
forum: General Help
---

### Post by Darkblood18 on 2010-04-29
Hi there. I´ve been trying to compile a third party software in Ubuntu (9.10 - 32 bit) using g++-4.4. The code worked fine in older versions of Ubuntu (which used older g++). The error I get is:
 
```

>> Compiling tmp/src/ExRootAnalysisDict.cc
tmp/src/ExRootAnalysisDict.cc:177: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.4/bits/stl_pair.h:67: error: provided for ‘template<class _T1, class _T2> struct std::pair’
tmp/src/ExRootAnalysisDict.cc:177: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.4/bits/stl_pair.h:67: error: provided for ‘template<class _T1, class _T2> struct std::pair’
tmp/src/ExRootAnalysisDict.cc:177: error: template argument 2 is invalid
tmp/src/ExRootAnalysisDict.cc:177: error: template argument 1 is invalid
tmp/src/ExRootAnalysisDict.cc:177: error: template argument 2 is invalid
tmp/src/ExRootAnalysisDict.cc:177: error: template argument 4 is invalid

```
 
The particular piece of code that seems to be generating that is (from lines 161 to 182, the long one is line 177 mentioned in the error)
 
```

#if !(defined(R__ACCESS_IN_SYMBOL) || defined(R__USE_SHADOW_CLASS))
      typedef ::ExRootFilter ExRootFilter;
      #else
      class ExRootFilter  {
         public:
         //friend XX;
         #if !(defined(R__ACCESS_IN_SYMBOL) || defined(R__USE_SHADOW_CLASS))
         typedef ::ExRootFilter::FilterExeption FilterExeption;
         #else
         class FilterExeption  {
            public:
            //friend XX;
         };
         #endif
 
         typedef ::std::map<int, ::TObjArray*, ::less<int>, ::allocator< ::pair<const int, ::TObjArray*> > > TCategoryMap;
         typedef ::std::map< ::ExRootClassifier*, ::pair< ::bool, ::map<int, ::TObjArray*, ::less<int>, ::allocator< ::pair<const int, ::TObjArray*> > > >, ::less< ::ExRootClassifier*>, ::allocator< ::pair< ::ExRootClassifier* const, ::pair< ::bool, ::map<int, ::TObjArray*, ::less<int>, ::allocator< ::pair<const int, ::TObjArray*> > > > > > > TClassifierMap;
         :: TSeqCollection* fCollection; //
         ::TIterator* fIter; //
         TClassifierMap fMap; //
      };
      #endif 

```Anyone has an idea of what´s going on? 
 
I´m a novice in c++, and I´m guessing there´s some change in parsing from older g++ to the current. I don´t know how to change the code to make it on par with new standards so I´ll be needing some workaround.
 
Thanks

---

