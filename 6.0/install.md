---
layout: default6
title: Installation
---

### Download and install

To use Joshua as a standalone decoder (with
[language packs](/language-packs/)), you only need to download and
install the decoder. There are no external dependencies.

1. Download Joshua

       curl -#L http://joshua-decoder.org/releases/6.0 > joshua-v6.0.tgz

1. Next, unpack it, set environment variables, and compile everything. You need to define the
`$JOSHUA` environment variable (which in turn requires `$JAVA_HOME`).

       tar xzf joshua-v6.0.tgz
       cd joshua-v6.0

       # for bash
       export JAVA_HOME=/path/to/java
       export JOSHUA=$(pwd)
       echo "export JOSHUA=$JOSHUA" >> ~/.bashrc
       
       # build everything
       ant

   (If you don't know what to set `$JAVA_HOME` to, try `/usr/java/default`).
   
   This compiles Joshua and also a number of support tools, such as KenLM and GIZA++.

1. [Download a model](/language-packes/) and start translating!

### Building new models

If you wish to build models for new language pairs from existing data
(such as the [WMT data](http://statmt.org/wmt14/)), you need to
install some additional dependencies.

1. For learning hierarchical models, Joshua includes a tool called [Thrax](/6.0/thrax.html), which
is built on Hadoop. If you have a Hadoop installation, make sure that the environment variable
`$HADOOP` is set and points to it. If you don't, Joshua will roll one out for you in standalone
mode. Hadoop is only needed if you plan to build new models with Joshua.

1. You will need to install Moses if either of the following applies to you:

    - You wish to build [phrase-based models](/6.0/phrase.html) (Joshua 6.0 includes a phrase-based
      decoder, but not the tools for building such a model)

    - You are building your own models (phrase- or syntax-based) and wish to use Cherry & Foster's
[batch MIRA tuner](http://aclweb.org/anthology-new/N/N12/N12-1047v2.pdf) instead of the included
MERT implementation, [Z-MERT](/6.0/zmert.html). 

    Follow [the instructions for installing Moses
here](http://www.statmt.org/moses/?n=Development.GetStarted), and then define the `$MOSES`
environment variable to point to the root of the Moses installation.

## More information

For more detail on the decoder itself, including its command-line options, see
[the Joshua decoder page](decoder.html).  You can also learn more about other steps of
[the Joshua MT pipeline](pipeline.html), including [grammar extraction](thrax.html) with Thrax and
Joshua's [efficient grammar representation](packing.html).

If you have problems or issues, you might find some help [on our answers page](faq.html) or
[in the mailing list archives](https://groups.google.com/forum/?fromgroups#!forum/joshua_support).

A [bundled configuration](bundle.html), which is a minimal set of configuration, resource, and script files, can be created and easily transferred and shared.
