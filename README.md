# Why?
Well, we (as in C++ developers) all heard about [boost](https://www.boost.org/), and hopefully using its libariries in our code. However, how well do we know what it has to offers?

In some cases, you can just look up things you need, and see if boost has a solution. For example, you need a regular expression libarary, and check what boost has to offer here (actually is has 2: [Regex](https://www.boost.org/doc/libs/1_69_0/libs/regex/doc/html/index.html) and [Xpressive](https://www.boost.org/doc/libs/1_69_0/doc/html/xpressive.html)). 

In other cases, you may have faced a problem that can be solved with your own code, because you didn't expect a "library" to exist for it. In many of these cases you were better off using code from boost, due to better: edge case handling, performance, thread safety etc., then your own. For example, in your code you needed a map in which you can lookup via either the key or the value, this could be implemented naively via 2 STL maps - still boost has a better implementation called a [bimap](https://www.boost.org/doc/libs/1_69_0/libs/bimap/doc/html/index.html).

An even more interesting case, are problems that you can't really figure out a good solution for. So, you modify your design to match what you can implement, even if you feel that it is not optimal. For example, you want to store objects in a conatiner, but want to pre-allocate them (e.g. due to high construction cost). You may feel that storing the objects in one place and the pointers to them in the container is a reasonable compromise (inspite of the level of indirection it inflicts), until you look at the [Intrusive](https://www.boost.org/doc/libs/1_69_0/doc/html/intrusive.html) library.

So, we shoud know boost better, but currently (version 1.69), there are [155 different libraries](https://www.boost.org/doc/libs/?view=condensed) in boost, and learning them all is impractical. 

This guide tries to provide a high level map of these libararies so it would be easier to know what you should look at and what could be safely skipped.

# What to Skip
There are 2 major categories of libraries that you can probably skip: 
 - Libaraies which are alleady in the standard. Boost did such a good job that many of its libaries and ideas were introduced into the C++11 standard. So, unless you are writing code that has to be C++03 compatible, you can probably ignore these libaraies. Note that the list of libraries listed as: [TR1](https://www.boost.org/doc/libs/?view=filtered_std-tr1) and [Proposal](https://www.boost.org/doc/libs/?view=filtered_std-proposal) probably fall into this category, but some refinements are needed, and will be detailed below.
 - Libraries which are used internally by boost developers. Unless you want to contribute to boost (which is something you should do), you can probably skip these.
 ## Already in C++11
 - [Array](https://www.boost.org/doc/libs/1_69_0/doc/html/array.html): use ```std::array```
 - [Bind](https://www.boost.org/doc/libs/1_69_0/libs/bind/doc/html/bind.html): use: ```std::bind```
 - [Hash](https://www.boost.org/doc/libs/1_69_0/doc/html/hash.html): covered by ```std::hash``` for basic types, if you want to hash more complex stuff (e.g. STL containers), check the boost library
 - [Function](https://www.boost.org/doc/libs/1_69_0/doc/html/function.html) and [Member Function](https://www.boost.org/doc/libs/1_69_0/doc/html/function.html): use ```std::function```
 - [Random](https://www.boost.org/doc/libs/1_69_0/doc/html/boost_random.html): use the stuff from the ```<random>``` header file
 - [Ref](https://www.boost.org/doc/libs/1_69_0/libs/core/doc/html/core/ref.html): use: ```std::ref``` and ```std::cref```
 - [Regex](https://www.boost.org/doc/libs/1_69_0/libs/regex/doc/html/index.html): use the stuff from the ```<regex>``` header file
 - [Tuple](https://www.boost.org/doc/libs/1_69_0/libs/tuple/doc/html/tuple_users_guide.html): use ```std::tuple```
 - [Type Traits](https://www.boost.org/doc/libs/1_69_0/libs/type_traits/doc/html/index.html): use the stuff from the ```<type_traits>``` header file
- [Unordered](https://www.boost.org/doc/libs/1_69_0/doc/html/unordered.html): use ```std::unordered_map/set/multimap/multiset```
- [Chrono](https://www.boost.org/doc/libs/1_69_0/doc/html/chrono.html): mostly covered by ```std::chrono```, but add some "CPU clocks" for: real/user/system and procees/thread times.
- [Thread](https://www.boost.org/doc/libs/1_69_0/doc/html/thread.html): use ```std::thread```, though there are some differences and extensions
- [Ratio](https://www.boost.org/doc/libs/1_69_0/doc/html/ratio.html): use ```std::ratio```
...
## Boost Internals 
...
# Learn as Needed
These libraries cover specific subjects, if you are interested in tese subjects, you should look into them:
- [DLL](https://www.boost.org/doc/libs/1_69_0/doc/html/boost_dll.html): open DLLs, SOs etc.
- [Stacktrace](https://www.boost.org/doc/libs/1_69_0/doc/html/stacktrace.html): creating backtrace of calls without using a debugger. May also look into C++11 nested exceptions for that

# Should Learn
...
