# Picture Status Background Selection

This context chooses a background for each generated status image while balancing
cached availability with direct retrieval latency.

## Language

**Background provider**:
A source of background-image candidates.

**No-preload provider**:
A provider explicitly selected to skip routine preloading.
_Avoid_: A fallback provider that happens to supply a candidate.

**Preloaded background**:
A candidate retained before a status-image request.

**Preload target**:
The non-negative desired count of preloaded backgrounds. Zero disables routine
background preloading.

**Fire retrieval**:
A one-candidate, immediate retrieval started when no preloaded background is
available.

**Late completion**:
A fire retrieval result that arrives after its original request has timed out
and remains available to a later request.

**Retry budget**:
The maximum consecutive routine preload attempts that finish without a
candidate. Any candidate resets the budget.

**Deferred recovery**:
Resuming routine preloading after any later image-retrieval call once its retry
budget is exhausted.
