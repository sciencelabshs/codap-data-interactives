# Robot Voices
This sonification plugin automatically generates unique timbres, or formants, from hierarchically-grouped data.

## Basic usage
1. Create a hierarchical grouping in a table by dragging an attribute, or multiple attributes, to the left side. 
2. Select `Context` and `Group by` entries. Note that `Group by` uses a data collection (i.e., a level in hierarchy) rather than an attribute. You should select a parent collection that has fewer number of cases. Finally, select `Pitch` attribute with numeric data type.
3. In the case table or graph, select several individual cases to hear the robot-like voices. While you can select a large number of cases in a group, it can get very loud and CPU intensive.

## What is going on?
When you set the `Group by` item, the plugin automatically generates a unique sound color for each group, indicated by colored spectral envelopes in the bottom half of the plugin. You may be able to hear the slight difference between individual cases from different groups. The spectral envelopes are generated by 1) calculating the aggregates of the group members (for numeric types, the mean value; for categorical types, the case count) as a parameter list 2) using this list in an inverse Mel-Frequency Cepstrum Coefficients (MFCC). MFCC is a technique to summarize perceptually-distinct timbres very often used in speech analysis. We do the inverse of MFCC to estimate the peaks of spectrum, and interpolate the areas between with the cosine interpolation to create a complete magnitude spectrum. 