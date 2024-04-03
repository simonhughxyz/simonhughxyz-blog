+++
title = "How I Made This Site"
date = "2024-04-03T13:43:26+01:00"
author = "Simon H Moore"
cover = ""
tags = ["hugo", "html"]
keywords = ["hugo", "html"]
description = ""
showFullContent = false
readingTime = false
hideComments = false
color = "" #color from the theme settings
+++

[hugo]: https://gohugo.io/
[kiss]: https://en.wikipedia.org/wiki/KISS_principle
[go]: https://go.dev/
[install-hugo]: https://gohugo.io/installation/
[scoop]: https://scoop.sh/
[chocolatey]: https://chocolatey.org/
[hugo themes]: https://themes.gohugo.io/
[hugo quickstart]: https://themes.gohugo.io/
[terminal]: https://hugothemesfree.com/a-simple-retro-theme-for-hugo/
[nginx]: https://www.nginx.com/
[github pages]: https://pages.github.com/
[github dns instructions]: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site

I have always believed in minimalism and the [KISS] principle, so when I wanted to make my own site and blog, I needed something that followed these ideals.

[Hugo] to the rescue!

# How does hugo work?

[Hugo] is a static site generator written in [Go], it is incredibly easy to set up and get going and you can write your content in plain old markdown. [Hugo] then takes you content/posts/blogs written in markdown and compiles them to html with a beautiful theme.

To use [hugo], you first need to install it, you can find the official documentation to do so [here][install-hugo], but if you are using linux, it will most likely be available in your distributions package manager, and on windows you can us [scoop] or [chocolatey] to install [hugo].

Once [Hugo] is installed, follow the [quickstart][hugo quickstart] to create a site and pick and install a hugo theme (of course you can make your own if you whish).
You can search for hugo themes on their official website [here][hugo themes].

After which it is as easy as creating some markdown files in the content folder and write about anything you want.

Note: its best to create the markdown files with the command `hugo new NAME-OF-FILE` as hugo will generate the appropriate metadata in the file for you.

[Hugo] comes with a inbuilt development server to preview your content, just run `hugo server` inside your sites root directory and then, in your browser, navigate to `http://localhost:1313` (the port might be different if `1313` is occupied, check the output of the command for the uri address).

Once you are happy with how your site looks and its content, simply run the `hugo` command inside your sites root directory and it will compile the site and generate all necessary files inside the `public` directory.

You can then host the `public` directory with your preferred web server such as [nginx].

# GitHub Pages
One easy and simple way to host your website for free is to use [github pages], this is what I did for my site.

What are the advantages of [github pages]?
1. its very easy to set up and maintain.
2. you can use `git` to update your website, simple commit your latest changes and push them to the repository.
3. its free.

But there are some disadvantages using [github pages], such as that it has minimal support for dynamic content and no support for server side code. But that is ok, since we are using [hugo], a static site generator.

To do so simply create a repository on your github account called `USERNAME.github.io` (where `USERNAME` is the username of your github account) and push the contents of the `public` folder inside your hugo site to said repository. 

You can then access your github page by navigating to `USERNAME.github.io` in your browser.

# I want to use my own domain
As cool as [github pages] is, it would be even cooler if you could use your own domain such as `simonhugh.xyz`, and you can.

All you need to do is purchase a domain from a domain register and create 4 new `A records` for the domain and set each to one of the four github IP addresses listed below:

    - 185.199.108.153
    - 185.199.109.153
    - 185.199.110.153
    - 185.199.111.153

You can find more help on how to do this by following the official github instructions [here][github dns instructions].

After you have done that, navigate to your [github pages] repository and navigate to setting -> pages and enter your domain in the `custom domain` field. Github will then verify that you DNS is set up properly, once it has, you should be able to view your [github pages] website by navigating to your custom domain.

Note: if it does not work, you might need to wait a while since it can take up to 48 hours to propagate the changes you made to your domains `A records`.
