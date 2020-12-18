# lighthouse-co2-action

A forkable repo, as an experiment in using github actions to git-scrape a site to record how well they perform in terms of accessibility, performance, and carbon emissions from transfer

# The big idea

We have tools like Website carbon, which is a really nice way into engaging with the issue of carbon emissions from the energy used to shift data from datacenters to your device.

And in the Green Web Foundation we've worked with the lovely people at Sitespeed [to build a sustainable web plugin](), to help understand the CO2 footprint of a website too, and _get some useful context specific tips on how to reduce it.

Using this, you can [create carbon dashboards for your websites, like how the wikipedia team do]()

But what if you want to track this, but don't want run a bunch of servers continually checking sites, but you still want to track how a site is scoring, and how to make it better?

You shouldn't need to run all your own infrastructure to do this, and if you're not doing indutrial level, big performance team type checking, it should still be possible to keep an eye on performance over time, and get pointers and how to improve a site.

This is the problem we're trying to solve with this repo. You fork the repo, update the site to check, and then switch on actions.

Every day, a github action:

- will check the site with lighthouse
- make a report available for you to download and compare to previous days
- store the report json into git, in a seperate branch, so you have a record of changes over time, and can recreate any report page for any run that was ever committed.

## How to use it

- fork the repo
- change the url that lighthouse is pointed at
- activate github actions for your new repo

That's it.

A cronjob will check the site for you every day, and every day, you'll have a single page report, like the one below you can share with anyone else in your team, showing how accessible the site is, how it scores in terms of perfomance, search engine visibility and so on, and how to improve it.



## Todo

- [ ] make the url easy to change, like an environment variable, instead having it hardcoded (good first issue!)
- [x] add the cronjob workflow, [so a lighthouse check can be made every day without you needing to remember](https://docs.github.com/en/free-pro-team@latest/actions/reference/events-that-trigger-workflows#scheduled-events)
- [ ] figure out how to make the lighthouse json report commit to the separate 'runs' branch, [see this post by Simon Willison on what git-scraping is, and why it's neat](https://simonwillison.net/2020/Oct/9/git-scraping/).
- [ ] add conversion from data tranferred, to CO2. Ideally, by adapting [@dvalezquez's lighthouse-plugin-co2 extension](https://github.com/dvelasquez/carbon-tools), to use [co2.js](https://github.com/thegreenwebfoundation/co2.js), it's in use on sitespeed.io already.
- [ ] add a way to check using [the TGWF grid-intensity npm module](https://github.com/thegreenwebfoundation/grid-intensity) to run the job when energy is greenest (running computers to check websites uses energy too, so try to do it when the grid is greenest!)
- [ ] oh, jeez, document this better
