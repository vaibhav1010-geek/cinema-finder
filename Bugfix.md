# Bug Fix: Nearby Cinemas Distance Issue

## Bug Description
The "Nearby Cinemas" view displayed cinemas that were significantly far away
(100km+) from the user's current location. These cinemas were incorrectly shown
as nearby with valid distance values.

## Root Cause
The application calculated and sorted distances correctly but did not apply
any maximum distance threshold. It simply sliced the nearest 15 cinemas,
regardless of how far away they were.

## Fix Implemented
A maximum distance constraint of 100km was introduced. Cinemas are now:
1. Sorted by distance
2. Filtered to include only those within 100km
3. Limited to a maximum of 15 results

If no cinemas are within 100km, an empty state is shown.

## Files Modified
- `src/hooks/nearbycinemas.js`

## Result
The Nearby Cinemas list and map markers now correctly reflect real proximity
to the user's location.
