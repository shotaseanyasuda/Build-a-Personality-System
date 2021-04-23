## Build-a-Personality-System
Build own personality system like MBTI using simple machine learning. 

Takes first 38,000 responses from a dataset of 1,000,000 responses to a 50 question questionaire based on the Big Five personality test.
I chose 38,000 because of GitHub's size limit for uploading files. 

The original datafile was called data-final.csv. I ran the following code to create the smaller, modified data file.
* `df = pd.read_csv('data-final.csv', delimiter="\t") `
* `df.head(38000).to_csv('data-final-modified.csv', Index=False)`

Results of text are displayed on graphs. These graphs will be displayed on a webserver.

## The original data file with 1,000,000 responses
If you want to download the original data file and run the program using 1,000,000 responses. 
https://www.kaggle.com/tunguz/big-five-personality-test

## If running on Visual Studio Code
You must change environment to 'base':conda. I used Python3.8.5 64-bit ('base':conda)
You must also install pandas,numpy, and sklearn.

## Information about the data file (copied and pasted from a README file from the above link)

This data was collected (2016-2018) through an interactive on-line personality test.
The personality test was constructed with the "Big-Five Factor Markers" from the IPIP. https://ipip.ori.org/newBigFive5broadKey.htm
Participants were informed that their responses would be recorded and used for research at the beginning of the test, and asked to confirm their consent at the end of the test.

The following items were presented on one page and each was rated on a five point scale using radio buttons. The order on page was was EXT1, AGR1, CSN1, EST1, OPN1, EXT2, etc.
The scale was labeled 1=Disagree, 3=Neutral, 5=Agree

1. EXT1	I am the life of the party.
2. EXT2	I don't talk a lot.
3. EXT3	I feel comfortable around people.
4. EXT4	I keep in the background.
5. EXT5	I start conversations.
6. EXT6	I have little to say.
7. EXT7	I talk to a lot of different people at parties.
8. EXT8	I don't like to draw attention to myself.
9. EXT9	I don't mind being the center of attention.
10. EXT10	I am quiet around strangers.
11. EST1	I get stressed out easily.
12. EST2	I am relaxed most of the time.
13. EST3	I worry about things.
14. EST4	I seldom feel blue.
15. EST5	I am easily disturbed.
16. EST6	I get upset easily.
17. EST7	I change my mood a lot.
18. EST8	I have frequent mood swings.
19. EST9	I get irritated easily.
20. EST10	I often feel blue.
21. AGR1	I feel little concern for others.
22. AGR2	I am interested in people.
23. AGR3	I insult people.
24. AGR4	I sympathize with others' feelings.
25. AGR5	I am not interested in other people's problems.
26. AGR6	I have a soft heart.
27. AGR7	I am not really interested in others.
28. AGR8	I take time out for others.
29. AGR9	I feel others' emotions.
30. AGR10	I make people feel at ease.
31. CSN1	I am always prepared.
32. CSN2	I leave my belongings around.
33. CSN3	I pay attention to details.
34. CSN4	I make a mess of things.
35. CSN5	I get chores done right away.
36. CSN6	I often forget to put things back in their proper place.
37. CSN7	I like order.
38. CSN8	I shirk my duties.
39. CSN9	I follow a schedule.
40. CSN10	I am exacting in my work.
41. OPN1	I have a rich vocabulary.
42. OPN2	I have difficulty understanding abstract ideas.
43. OPN3	I have a vivid imagination.
44. OPN4	I am not interested in abstract ideas.
45. OPN5	I have excellent ideas.
46. OPN6	I do not have a good imagination.
47. OPN7	I am quick to understand things.
48. OPN8	I use difficult words.
49. OPN9	I spend time reflecting on things.
50. OPN10	I am full of ideas.

The time spent on each question is also recorded in milliseconds. These are the variables ending in _E. This was calculated by taking the time when the button for the question was clicked minus the time of the most recent other button click.

# some metadata collected from the questionaire
- dateload    The timestamp when the survey was started.
- screenw     The width the of user's screen in pixels
- screenh     The height of the user's screen in pixels
- introelapse The time in seconds spent on the landing / intro page
- testelapse  The time in seconds spent on the page with the survey questions
- endelapse   The time in seconds spent on the finalization page (where the user was asked to indicate if they has answered accurately and their answers could be stored and used for research. Again: this dataset only includes users who answered "Yes" to this question, users were free to answer no and could still view their results either way)
- IPC         The number of records from the user's IP address in the dataset. For max cleanliness, only use records where this value is 1. High values can be because of shared networks (e.g. entire universities) or multiple submissions
- country     The country, determined by technical information (NOT ASKED AS A QUESTION)
- lat_appx_lots_of_err    approximate latitude of user. determined by technical information, THIS IS NOT VERY ACCURATE. Read the article "How an internet mapping glitch turned a random Kansas farm into a digital hell" https://splinternews.com/how-an-internet-mapping-glitch-turned-a-random-kansas-f-1793856052 to learn about the perils of relying on this information
- long_appx_lots_of_err   approximate longitude of user

