---
title: "urgent -- error installing ns2 on ubuntu 7.04"
date: 2011-01-23
forum: General Help
---

### Post by king2k on 2011-01-23
i am using ubuntu 7.04 and ns2.26 (for some reasons i have to use these versions)

i receive this error, and i need quick help please. thanks

```
diffusion3/lib/dr.o: In function `std::list<CallbackEntry*, std::allocator<CallbackEntry*> >::_M_insert(std::_List_iterator<CallbackEntry*>, CallbackEntry* const&)'
dr.cc:(.text._ZNSt4listIP13CallbackEntrySaIS1_EE9_M_insertESt14_List_iteratorIS1_ERKS1_[std::list<CallbackEntry*, std::allocator<CallbackEntry*> >::_M_insert(std::_List_iterator<CallbackEntry*>, CallbackEntry* const&)]+0x29): undefined reference to `std::_List_node_base::hook(std::_List_node_base*)'
diffusion3/lib/dr.o: In function `std::list<FilterEntry*, std::allocator<FilterEntry*> >::_M_insert(std::_List_iterator<FilterEntry*>, FilterEntry* const&)':
dr.cc:(.text._ZNSt4listIP11FilterEntrySaIS1_EE9_M_insertESt14_List_iteratorIS1_ERKS1_[std::list<FilterEntry*, std::allocator<FilterEntry*> >::_M_insert(std::_List_iterator<FilterEntry*>, FilterEntry* const&)]+0x29): undefined reference to `std::_List_node_base::hook(std::_List_node_base*)'
diffusion3/lib/dr.o: In function `std::list<HandleEntry*, std::allocator<HandleEntry*> >::_M_insert(std::_List_iterator<HandleEntry*>, HandleEntry* const&)':
dr.cc:(.text._ZNSt4listIP11HandleEntrySaIS1_EE9_M_insertESt14_List_iteratorIS1_ERKS1_[std::list<HandleEntry*, std::allocator<HandleEntry*> >::_M_insert(std::_List_iterator<HandleEntry*>, HandleEntry* const&)]+0x29): undefined reference to `std::_List_node_base::hook(std::_List_node_base*)'
diffusion3/lib/dr.o: In function `std::list<DiffusionIO*, std::allocator<DiffusionIO*> >::_M_insert(std::_List_iterator<DiffusionIO*>, DiffusionIO* const&)':
dr.cc:(.text._ZNSt4listIP11DiffusionIOSaIS1_EE9_M_insertESt14_List_iteratorIS1_ERKS1_[std::list<DiffusionIO*, std::allocator<DiffusionIO*> >::_M_insert(std::_List_iterator<DiffusionIO*>, DiffusionIO* const&)]+0x29): undefined reference to `std::_List_node_base::hook(std::_List_node_base*)'
collect2: ld returned 1 exit status
make: *** [ns] Error 1
Ns make failed!
See http://www.isi.edu/nsnam/ns/ns-problems.html for problems
```

---

