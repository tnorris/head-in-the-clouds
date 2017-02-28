# Intro
## Me
- Tom Norris &lt;tom.norris@acquia.com&gt; github.com/tnorris
- Acquian for almost 3 years.
- About half my tenure on Operations, most recent half has been on Infrastructure Services Tools Team
- Did ITOps at `job.last`
- Did Managed IT at `jobs[-2]`

## DevOps is How To
- Avoid stepping on each other's toes
- Speed up cycle times
- Continuously improve work life
- Use data to make decisions (win arguments)

Big focus on automation

# Why Do You Want DevOps
## Management:
- The Industry's Best Standard
- Cut time to resolution; with enough investment, _orders_ of magnitude.
- Better availability from your company's services
- Increase throughput while reducing the inventory and operating expense (The Goal!) (reduce COGS)
- Happier employees

## Contributors:
- The Industry's Best Standard
- Automate away menial tasks that eat away at your soul
- (we have multiple products with deployment runbooks that say, `get a snack`)
- Reduce total number of defects
- Ability to squish defects faster
- Reduction of duplicated effort!

# How Do we get there?
## Prereqs
- Ticketing System
- Monitoring
- Time Series Database

## The Three Ways
- How to incrementally adopt DevOps. Developed by Gene Kim et al

### Systems Thinking
- DevOps is not the goal. The goal is profit. DevOps is the way to get there.
- Map out all of the value streams that are enabled by your department. 
- Don't pass along defects (Have empathy for your clients)

### Amplify Feedback Loops
- Shorten feedback loops. Get cycle time down, get departments talking to each other
- Let the left hand know what the right hand is doing

### Culture of Continual Experimentation and Learning
- Blameless post mortems
- Root Cause Analysis
- Learn from your mistakes
- Improve your processes
- Get rid of processes that don't make sense


## Identifiy the Constraint
###  Metrics
#### Time Spent On Business projects
- Features for product
- adding a new customer-accessible version of PHP to the hosting platform
- creating a new spamfighting service
- getting PDF reports for clients

#### Time Spent On Internal Projects
These are things like...
- improving process
- making integration-tests faster
- cleaning up that ENGINEERING_ONBOARDING confluence page
- writing runbooks to deploy new TLS certificates to load balancers
- this talk
- Root Cause Analysis

#### Time Spent On Operational Change
- rack 'n stack
- putting servers up in a datacenter
- running scripts to spin up cloud primitives
- every time you type `puppet agent -t` or `ansible-playbook`
- rsyncing your `.war` files and HUPping tomcat
- giving JIRA more heap

#### Time Spent On Toil
- Waste and firefighting
- service is down
- server is on fire
- lightning storm took out us-east-1, please migrate fleet to us-west-2
- cutely named exploit of the month (time to reboot the fleet!)

### Dev Team (ideal world)
- Business, Internal, Change, Toil
Product wants you to keep making new features, but tech. debt still needs to get paid. You don't spend much time to deploy (See snack comment); you get paged once in a while (rotation)

### Ops Team (ideal world)
- Internal, Business, Change, Toil
Hacking on new projects to improve the business, like better monitoring, automating incident response. Teams want new hardware, but there's process and it's predictable. Firefighting is still a part of life, but normal work continues, even when the next rebootarama happens

### Cycle time
How long do I have to wait for a class of work to get gone?

### Throughput
Amount of work done. Storypoints/issues/new-customers-onboarded/etc

### Frequency by request type
This is how you know what to automate first

### Frequency by root cause
Use this to figure out what product defect is causing the most pain

### Downstream defects (Reopened Issues, Bugs)
Use this to figure out when you're stepping on other teams' (or even worse: customers') toes

### Time tracking (IT/Ops: average 5-6hours/day, SRE: track all time on toil, Dev: sprints)
#### For Ops/IT,
- people gotta eat, meet, get interrupted by folks asking, 'hey did you get my email about the thing?', use the restroom, deal with landlord
- less than that, and you can't really trust your metrics
- more than that, people are going to burn out
- If &gt; 25% of your IT or Ops teams are firefighting at the same time, at any given time, something is horribly wrong (paraphrased Tom Limoncelli)

#### For SRE:
- If more than half your time is on firefighting, pull in your dev team, they get to help!

#### For Dev:
- Have some sprint buffer to deal with bugs and other critical things that pop up during your sprints
- Acquia Infra. Services Tools Team does 20%
- This will make your embedded SRE, Ops Team, or IT Team much happier with your team

### Operational Load is the batting average of IT metrics
- Amount of time you spend keeping your boat afloat
- Google says cap it at 50%
- (See 'wait time' graph from The Phoenix Project)

## A Note On Talking To Business Folks
- Dollars per second is the most effective metric.
- You can use unit conversions to get from operational load to dollars/second.
- Dollars per quarter is the 2nd most effective.

# Document Common Processes
Once your team gets into the habbit of using runbooks (and continuously improving them as things change),
- tasks become accessible to the entire team
- you get escalated to less often, because you can point to the docs (and say READ THE DOCS)

Write runbooks for the most frequently occuring task, first. Use `/[:alpha:]*scouts/` camping rules, and Kaizen/3rd-way, when you stub your toe, fix the runbook!

# Automate Common Processes
- You *must* have runbooks before you automate.

# Streamline ticket creation
Turns out you can get fancy with JIRA tickets, requiring things like 
- Component
- Severity
- Hosting Environment
- Customer Impact
- Customer Deadline

or for a Sprint team
- Epic
- Sprint
- Stakeholder
- Release notes required?
- (don't forget to click 'move to kanban!')

People are pretty bad at remembering all these things. 
Streamline the process by making a portal to your ticketing system.
Start off with the most frequent tasks, that way you get
- consistent tickets
- reduced back-and-forth ("you didn't mark it as critical so we didn't realize the customer needs it today!")
- reduced time-to-completion (due to the above)

You don't have to go crazy and build a service here. A PoC can be done in Confluence by creating chose-your-own-adventure links to confluence pages that eventually link to Jira's `createTicket?with=url&params=to&set=your&custom=fields`

# Awesome Books
- The Phoenix Project
- The Practice of Cloud System Administration
- Site Reliability Engineering

# Awesome Talks
- Amin Astaneh - People Metrics: https://www.youtube.com/watch?v=sWMy6aNY_XA
